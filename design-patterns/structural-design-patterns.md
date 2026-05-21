# Structural Design Patterns — Comprehensive and Detailed Guide

## 1. Introduction to Structural Patterns
Structural design patterns are essential tools in software engineering that focus on how classes and objects are composed to form larger, more complex structures. These patterns ensure that when these entities are combined, the resulting system remains flexible, efficient, and easy to maintain.

*   **Definition:** Patterns that exploit the composition of classes and objects to form larger structures while keeping those structures independent and decoupled.
*   **Purpose:** They facilitate the creation of relationships between entities, allowing independently developed class libraries to work together seamlessly.
*   **Key Principle:** These patterns prioritize **composition over inheritance**. While inheritance is a static, compile-time relationship, object composition allows for dynamic, run-time flexibility.
*   **Class vs. Object Patterns:**
    *   **Structural Class Patterns** use inheritance to compose interfaces or implementations (e.g., Class Adapter).
    *   **Structural Object Patterns** describe ways to assemble objects to realize new functionality at run-time (e.g., Object Adapter, Decorator).

---

## 2. Adapter (Wrapper)
The Adapter pattern acts as a bridge between two incompatible interfaces.

*   **Problem:** Two classes cannot work together because their interfaces are incompatible. This often occurs when trying to integrate a new library or a legacy system without modifying its original source code.
*   **Solution:** A separate "Adapter" class is created that converts the interface of an existing class (**Adaptee**) into the interface expected by the client (**Target**).
*   **Example:** Integrating a legacy payment system into a modern e-commerce platform, or using a power adapter to connect a USB-C cable to a microUSB port.

### Java Implementation: Object Adapter
```java
// Target Interface expected by the client
interface ModernPaymentProcessor {
    void processPayment(double amount);
}

// Adaptee: The legacy system with an incompatible interface
class LegacyPaymentSystem {
    void executeTransaction(float val) {
        System.out.println("Processing legacy payment: " + val);
    }
}

// Adapter: Translates ModernPaymentProcessor calls to LegacyPaymentSystem
class PaymentAdapter implements ModernPaymentProcessor {
    private LegacyPaymentSystem legacySystem; // Composition: contains the adaptee

    public PaymentAdapter(LegacyPaymentSystem legacySystem) {
        this.legacySystem = legacySystem;
    }

    @Override
    public void processPayment(double amount) {
        // Converts double to float and calls the legacy method
        legacySystem.executeTransaction((float) amount);
    }
}
```
**Real-World Usage:**
*   **Spring Data JPA:** Uses adapters to allow various database drivers to work with a unified repository interface.
*   **Android:** `RecyclerView.Adapter` acts as a bridge between data sources and the UI views.

---

## 3. Decorator
The Decorator pattern allows for the dynamic addition of responsibilities to an object without altering its structure or affecting other instances of the same class.

*   **Problem:** Extending functionality through subclassing leads to an "exponential rise" in the number of classes when multiple independent extensions are required.
*   **Solution:** A wrapper class that implements the same interface as the object it wraps, delegating requests to the original object while adding behavior before or after the call.
*   **Example:** A coffee shop system where a base coffee can be "decorated" with milk, sugar, or chocolate.

### Java Implementation
```java
// Component Interface
interface Coffee {
    double getCost();
    String getDescription();
}

// Concrete Component
class SimpleCoffee implements Coffee {
    public double getCost() { return 2.0; }
    public String getDescription() { return "Simple coffee"; }
}

// Base Decorator
abstract class CoffeeDecorator implements Coffee {
    protected Coffee decoratedCoffee; // Reference to the wrapped object

    public CoffeeDecorator(Coffee coffee) { this.decoratedCoffee = coffee; }
    public double getCost() { return decoratedCoffee.getCost(); }
    public String getDescription() { return decoratedCoffee.getDescription(); }
}

// Concrete Decorator
class MilkDecorator extends CoffeeDecorator {
    public MilkDecorator(Coffee coffee) { super(coffee); }

    public double getCost() { return super.getCost() + 0.5; } // Adds cost
    public String getDescription() { return super.getDescription() + ", milk"; } // Adds description
}
```
**Real-World Usage:**
*   **Java I/O:** `BufferedReader` wraps `FileReader` to add buffering capabilities.
*   **Angular:** Uses Pipes to decorate data in templates without changing the underlying logic.

---

## 4. Facade
The Facade pattern provides a simplified, unified interface to a complex subsystem.

*   **Problem:** A subsystem consists of many interdependent classes, making it difficult for clients to use or understand.
*   **Solution:** A single "Facade" class provides a high-level interface that delegates work to the appropriate classes within the subsystem.
*   **Example:** A "VideoConverter" facade that hides the complexities of various codecs, audio compressors, and file bitrates.

### Java Implementation
```java
class VideoConverter {
    public void convert(String filename, String format) {
        // The Facade hides these complex internal interactions
        VideoFile file = new VideoFile(filename);
        Codec sourceCodec = CodecFactory.extract(file);
        Codec destinationCodec = (format.equals("mp4")) ? new MPEG4Codec() : new OggCodec();

        VideoBuffer buffer = BitrateReader.read(file, sourceCodec);
        VideoBuffer result = BitrateReader.convert(buffer, destinationCodec);
        System.out.println("Conversion complete.");
    }
}
```
**Real-World Usage:**
*   **SLF4J:** A facade over various logging frameworks (Log4j, Logback).
*   **JDBC DriverManager:** Simplifies the process of connecting to different databases through a single entry point.

---

## 5. Proxy
The Proxy pattern provides a surrogate or placeholder for another object to control access to it.

*   **Problem:** Access to an object needs to be controlled, audited, or delayed (e.g., if the object is resource-intensive to create).
*   **Solution:** A Proxy class implements the same interface as the **RealSubject**. It maintains a reference to the real object and intercepts client calls.
*   **Types of Proxies:**
    *   **Virtual Proxy:** Lazy loading for heavy objects (e.g., high-resolution images).
    *   **Protection Proxy:** Controls access based on permissions.
    *   **Remote Proxy:** Represents an object in a different address space (e.g., ATM communicating with a bank server).

### Java Implementation: Virtual Proxy
```java
interface Image {
    void display();
}

class RealImage implements Image {
    private String filename;
    public RealImage(String filename) {
        this.filename = filename;
        loadFromDisk(); // Expensive operation
    }
    private void loadFromDisk() { System.out.println("Loading " + filename); }
    public void display() { System.out.println("Displaying " + filename); }
}

class ProxyImage implements Image {
    private RealImage realImage;
    private String filename;

    public ProxyImage(String filename) { this.filename = filename; }

    public void display() {
        if (realImage == null) {
            realImage = new RealImage(filename); // Lazy initialization
        }
        realImage.display();
    }
}
```
**Real-World Usage:**
*   **Hibernate:** Uses proxies for "lazy loading" of database entities.
*   **Spring AOP:** Uses proxies to apply "aspects" like transaction management or logging.

---

## 6. Composite
The Composite pattern allows you to treat individual objects and groups of objects uniformly.

*   **Problem:** Systems need to represent tree-like part-whole hierarchies (e.g., folders containing files and other folders).
*   **Solution:** Both individual elements (**Leaf**) and containers (**Composite**) implement a common interface.
*   **Example:** A graphic editor where a "Picture" (composite) can contain "Lines" or "Circles" (leaves), and both can be "drawn" using the same command.

### Java Implementation
```java
interface Graphic {
    void draw();
}

class Circle implements Graphic {
    public void draw() { System.out.println("Drawing a Circle"); }
}

class CompositeGraphic implements Graphic {
    private List<Graphic> children = new ArrayList<>();

    public void add(Graphic g) { children.add(g); }

    public void draw() {
        for (Graphic child : children) {
            child.draw(); // Recursively calls draw on all children
        }
    }
}
```
**Real-World Usage:**
*   **DOM (Document Object Model):** Represents HTML elements as a tree of nodes.
*   **UI Frameworks:** Swing and AWT components use this to manage nested containers.

---

## 7. Bridge
The Bridge pattern decouples an abstraction from its implementation so that both can vary independently.

*   **Problem:** Permanent binding between an abstraction and its implementation makes it difficult to extend both hierarchies.
*   **Solution:** Use composition to link an abstraction to an implementation interface.
*   **Example:** A "Remote Control" abstraction that works across different "Device" implementations (TV, Radio).
*   **Real-World Usage:** **JDBC** serves as a bridge between an application (abstraction) and specific database drivers (implementation).

---

## 8. Flyweight
The Flyweight pattern reduces memory usage by sharing common data between a large number of similar objects.

*   **Problem:** An application uses a vast number of objects, leading to high storage costs and memory overhead.
*   **Solution:** Separate state into **Intrinsic** (shared, invariant data) and **Extrinsic** (unique, context-dependent data). Shared data is stored in a single flyweight object.
*   **Example:** A text editor storing thousands of characters; the font type and size (intrinsic) are shared, while the position (extrinsic) varies.
*   **Real-World Usage:** The **String Pool** and **Integer Cache** in Java.

---

## 9. Comparative Analysis of Structural Patterns

| Pattern | Primary Problem | Type | Use When | Avoid When |
| :--- | :--- | :--- | :--- | :--- |
| **Adapter** | Incompatible interfaces | Class/Object | Retrofitting existing classes | Changing original code is easy |
| **Bridge** | Abstraction tied to implementation | Object | Independent variation needed | Simple hierarchy is sufficient |
| **Composite** | Part-whole hierarchies | Object | Treating groups as individuals | Uniformity is not required |
| **Decorator** | Adding dynamic behavior | Object | Subclassing leads to class explosion | Interface is constantly changing |
| **Facade** | Complex subsystems | Object | Simple interface is needed | Subsystem is simple and stable |
| **Flyweight** | High memory usage | Object | Many similar, small objects | Identity of objects is critical |
| **Proxy** | Access control/Indirection | Object | Lazy loading or remote access | Direct access is efficient |

**Key Rules of Thumb:**
*   **Adapter** provides a *different* interface to its subject; **Proxy** provides the *same* interface; **Decorator** provides an *enhanced* interface.
*   **Adapter** is usually retrofitted after a system is designed; **Bridge** is designed up-front.
*   **Facade** defines a *new* interface; **Adapter** reuses an *old* interface.

---

## 10. Conclusion
Structural patterns are fundamental to building scalable, flexible software. They align closely with **SOLID principles**:
*   **Single Responsibility Principle (SRP):** Patterns like Decorator and Proxy allow classes to focus on their primary concern while delegating auxiliary tasks.
*   **Open-Closed Principle (OCP):** Decorators and Adapters allow systems to be extended without modifying existing source code.
*   **Dependency Inversion Principle (DIP):** Bridge and Adapter facilitate depending on abstractions rather than concrete implementations.

Choosing the right pattern requires analyzing whether the goal is to simplify (Facade), extend (Decorator), reconcile (Adapter), or optimize (Flyweight).

---

## Study Guide: Practice and Review

### Short-Answer Quiz
1.  What is the difference between an Object Adapter and a Class Adapter?
2.  In the Flyweight pattern, what is the difference between intrinsic and extrinsic state?
3.  Why is the Decorator pattern considered a memory-efficient alternative to subclassing?
4.  Which structural pattern is most likely to be implemented as a Singleton?
5.  What problem does the "Design for Transparency" approach solve in the Composite pattern?

### Essay Questions for Deeper Exploration
1.  **Composition vs. Inheritance:** Discuss how structural design patterns utilize composition to overcome the limitations of static inheritance hierarchies. Provide examples from the Decorator and Bridge patterns.
2.  **Interface Evolution:** Compare the Facade and Adapter patterns in the context of system evolution. How does each handle the challenge of changing requirements or integrating legacy code?
3.  **Proxy Scenarios:** Analyze the trade-offs of using a Virtual Proxy for lazy loading. In what scenarios might the overhead of a proxy outweigh its benefits?

### Glossary of Important Terms
*   **Adaptee:** The existing class with an incompatible interface that needs adapting.
*   **Aggregation:** A "has-a" relationship where objects are treated as a group but exist independently.
*   **Intrinsic State:** Data shared across multiple flyweight objects that remains constant regardless of context.
*   **Lazy Loading:** An optimization technique where the initialization of an object is deferred until it is actually needed (commonly implemented via a Virtual Proxy).
*   **Leaf:** An individual element in a Composite structure that has no children.
*   **Wrapper:** An alternative name for the Adapter and Decorator patterns, indicating that they "wrap" an object to provide a different or enhanced interface.