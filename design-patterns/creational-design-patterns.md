# Patrones de Diseño Creacionales — Guía completa y detallada

## 1. Introduction to Creational Patterns

Creational design patterns are fundamental software engineering solutions that focus on **object creation mechanisms**. Their primary goal is to create objects in a manner suitable to the situation, providing increased flexibility and reuse of existing code.

*   **Definition:** These patterns abstract the instantiation process, controlling how objects are created rather than allowing a system to instantiate objects directly using the `new` operator.
*   **Purpose:** They decouple a client from the knowledge of which concrete classes need to be instantiated. This ensures that the system is independent of how its objects are created, composed, and represented.
*   **Problem Solved:** Hard-coding object creation (using `new`) creates a rigid coupling between classes. This makes it difficult to change instantiations later, prevents reusability, and complicates testing because real objects cannot easily be replaced with mock objects.
*   **Advantages:**
    *   **Flexibility:** Provides control over the "what, who, how, and when" of object creation.
    *   **Maintainability:** Hides implementation details of class libraries.
    *   **Runtime Specification:** Allows instantiations to be specified at runtime.

---

## 2. Singleton

The **Singleton** pattern ensures that a class has only one instance and provides a global point of access to that instance.

*   **Problem:** Some situations require exactly one object to coordinate actions across a system (e.g., to prevent conflicting access to a shared resource).
*   **Solution:** Hide the constructor by making it private and provide a static method that manages and returns the single instance.
*   **Detailed Examples:** 
    *   **Logger:** A centralized point where all system components write messages.
    *   **Database Connections:** Managing a single shared pool or connection.
    *   **Configuration Settings:** A global object that holds application-wide parameters.
*   **Java Implementation Logic:**
    *   **Private Static Variable:** Holds the unique instance.
    *   **Private Constructor:** Prevents external instantiation.
    *   **Static Method:** Returns the instance, often utilizing **Lazy Initialization** (creating it only when first requested).

```java
// Example of Thread-Safe Singleton with Double-Checked Locking
public class DatabaseConnection {
    private static volatile DatabaseConnection instance;

    private DatabaseConnection() {} // Private constructor

    public static DatabaseConnection getInstance() {
        if (instance == null) {
            synchronized (DatabaseConnection.class) {
                if (instance == null) {
                    instance = new DatabaseConnection();
                }
            }
        }
        return instance;
    }
}
```
*   **Good Practices & Criticism:** While useful for lazy allocation, Singletons are sometimes criticized as an "anti-pattern" because they introduce global state, increase coupling, and can make unit testing difficult.

---

## 3. Factory Method

The **Factory Method** pattern defines an interface for creating an object but allows subclasses to decide which class to instantiate.

*   **Problem:** A class cannot anticipate the type of objects it must create, or it wants to delegate that responsibility to its subclasses.
*   **Solution:** Create a separate method for creating objects (the factory method) and have subclasses override this method to return the specific product.
*   **Detailed Examples:** 
    *   **Maze Game:** A `MazeGame` class might have a `makeRoom()` method. The `OrdinaryMazeGame` subclass returns `OrdinaryRoom`, while the `MagicMazeGame` subclass returns `MagicRoom`.
    *   **Document Creator:** An application handles various document types (PDF, Word) by calling a creator method that returns the appropriate concrete document object.
*   **Implementation Logic:**
    *   **Creator:** Declares the factory method.
    *   **Concrete Creator:** Overrides the factory method to return an instance of a Concrete Product.

```java
// Logic: Subclasses redefine object creation
public abstract class MazeGame {
    public MazeGame() {
        Room room = makeRoom(); // Factory Method call
    }
    protected abstract Room makeRoom();
}

public class MagicMazeGame extends MazeGame {
    @Override
    protected Room makeRoom() {
        return new MagicRoom();
    }
}
```

---

## 4. Abstract Factory

The **Abstract Factory** pattern provides an interface for creating families of related or dependent objects without specifying their concrete classes.

*   **Problem:** A system needs to be independent of how its products are created and needs to enforce that objects from the same family are used together.
*   **Solution:** Define an interface with a group of factory methods, one for each type of product in the family.
*   **Detailed Examples:**
    *   **Multi-platform UI:** A factory for creating "Windows" widgets (buttons, windows) vs. a factory for "Mac" widgets.
    *   **Document Themes:** A `DocumentCreator` providing `createLetter()` and `createResume()`. `FancyDocumentCreator` produces `FancyLetter` and `FancyResume`, while `ModernDocumentCreator` produces the modern variants.
*   **Implementation Logic:** The client uses the abstract interface of the factory to get products. It never knows which concrete factory (e.g., Windows vs. Linux) it is using.

---

## 5. Builder

The **Builder** pattern separates the construction of a complex object from its representation, allowing the same construction process to create different representations.

*   **Problem:** Objects requiring many optional parameters can lead to "telescoping constructors" (constructors with long lists of parameters).
*   **Solution:** Encapsulate the creation and assembly of parts in a separate **Builder** object. A **Director** class manages the construction steps.
*   **Detailed Examples:** 
    *   **Bicycle Assembly:** A Director follows steps to build a bicycle, but the specific Builder determines if it’s a mountain bike or a racing bike.
    *   **Pizza Construction:** Steps to add dough, sauce, and toppings can result in different pizza types depending on the builder used.
*   **Key Components:**
    *   **Director:** Knows the sequence of steps.
    *   **Builder:** Provides the interface for building parts.
    *   **Concrete Builder:** Implements the steps and returns the final product.

---

## 6. Prototype

The **Prototype** pattern creates new objects by cloning a prototypical instance.

*   **Problem:** Object creation via `new` might be prohibitively expensive or complex, or the specific types of objects to create are determined at runtime.
*   **Solution:** Specify the kinds of objects to create using a "prototypical" instance and create new objects by copying this prototype.
*   **Detailed Examples:**
    *   **Cell Division:** Like mitosis, an existing cell acts as the prototype to create an identical copy.
    *   **Bank Account Management:** Cloning an object containing account information to perform transactions while preserving the original data.
*   **Implementation Logic:** The client calls a `clone()` method on the prototype object instead of using the `new` operator.
*   **Good Practices:** Use cloning when you need a duplicate object at runtime that accurately reflects the original object's current state, rather than just its default class values.

---

## 7. Comparative Analysis of Creational Patterns

| Pattern | Main Problem | When to Use | When to Avoid | Real Example |
| :--- | :--- | :--- | :--- | :--- |
| **Singleton** | Multiple instances coordinate poorly. | Exactly one instance needed (e.g., Global state). | When it creates hidden dependencies/hurts testing. | Logger, Config. |
| **Factory Method** | Subclasses need to decide object type. | When a class doesn't know what subclasses it will need. | Simple creation where inheritance is overkill. | HTML5 `createElement`. |
| **Abstract Factory** | Creating families of related objects. | When a system must work with various families of products. | When adding new products requires changing the interface. | Multi-platform UI widgets. |
| **Builder** | Construction of complex objects. | When an object has many parts or optional parameters. | For simple objects with few attributes. | Bicycle assembly. |
| **Prototype** | Cloning expensive/dynamic objects. | When cost of `new` is high or types are dynamic. | When objects don't support cloning or have complex circular refs. | Cell cloning. |

### Decision Diagram (Textual)
1. Need exactly one instance? → **Singleton**
2. Need to clone an existing object? → **Prototype**
3. Construction involves many steps/complex parts? → **Builder**
4. Need to create a single product but let subclasses choose the type? → **Factory Method**
5. Need to create a whole family of related products? → **Abstract Factory**

---

## 8. Conclusion

Creational patterns are essential for maintaining the **Open-Closed Principle (OCP)** and **Dependency Inversion Principle (DIP)**. By delegating the responsibility of instantiation to specialized objects, developers can create systems that are easier to extend and test. 

While designs often start with the simpler **Factory Method**, they frequently evolve toward **Abstract Factory**, **Prototype**, or **Builder** as more flexibility is required. These patterns are widely implemented in modern frameworks to manage object lifecycles and simplify complex configurations.

---

## Study Guide: Review & Practice

### Short-Answer Quiz
1.  Which pattern is specifically designed to solve the "telescoping constructor" problem?
2.  What is the main difference between **Factory Method** and **Abstract Factory** regarding the number of products created?
3.  Why is a private constructor necessary in the **Singleton** pattern?
4.  In the **Prototype** pattern, what is the name of the method used to create a copy of an object?
5.  Which principle does the **Factory Method** support by allowing a class to be independent of the concrete products it creates?

### Essay Questions
1.  **Evolution of Design:** Explain the typical progression of a software design from using a simple Factory Method to more complex patterns like Abstract Factory or Builder. What triggers this evolution?
2.  **The Singleton Controversy:** Discuss why the Singleton pattern is often viewed as an anti-pattern. How does it impact unit testing and the Single Responsibility Principle?
3.  **Composition vs. Inheritance:** Compare how the Factory Method (relying on inheritance) and the Abstract Factory (relying on object composition) achieve the goal of decoupling object creation from usage.

---

## Glossary of Terms

*   **Concrete Creator:** A class that implements the creator interface and actually instantiates a specific product.
*   **Director:** A class in the Builder pattern that controls the construction process but does not know the internal details of the product.
*   **Double-Checked Locking:** A software practice used in Singletons to reduce overhead by checking the locking criterion without actually acquiring the lock unless necessary.
*   **Gang of Four (GOF):** The authors (Gamma, Helm, Johnson, Vlissides) of the seminal 1994 book *Design Patterns*.
*   **Lazy Initialization:** A tactic of delaying object creation until the first time the object is actually needed.
*   **Prototypes:** Initialized instances used as a template to be copied or cloned.
*   **Varying Representation:** The ability of the Builder pattern to create different types of products using the same construction process.