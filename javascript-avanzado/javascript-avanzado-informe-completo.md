# JavaScript Data Structures and Object-Oriented Programming: Comprehensive Briefing

## Executive Summary
This document provides a technical synthesis of JavaScript's advanced programming capabilities, focusing on Object-Oriented Programming (OOP) paradigms, built-in collections, and complex data structures. Based on source analysis, JavaScript has evolved from a prototype-based language into one that supports robust class-based hierarchies, enabling efficient encapsulation and inheritance. Key data structures—including Linked Lists, Binary Search Trees, and Graphs—are explored alongside the iteration protocols and error-handling mechanisms that form the backbone of modern JavaScript development.

---

## 1. Object-Oriented Programming (OOP)
JavaScript uses classes as templates for creating objects, encapsulating data, and defining behaviors. While classes are an abstraction over prototypical inheritance, they provide a clearer syntax for developers familiar with Java or C#.

### Core Concepts
*   **Classes and Constructors:** The `constructor()` method is a special function used to initialize object properties. It is executed automatically when a new instance is created via the `new` operator.
*   **Encapsulation (Private Fields):** Private fields, denoted by the `#` prefix, are inaccessible outside the class. This "hard private" feature ensures that internal data structures cannot be manipulated or broken by external logic.
*   **Getters and Setters:** Accessor properties allow methods to be treated like properties, providing an ergonomic way to read or validate data.
*   **Inheritance:** Using the `extends` keyword, a derived class inherits all public methods and properties from a parent class. The `super()` function must be called in the constructor of a derived class to initialize the parent's logic.

| Feature | Syntax | Description |
| :--- | :--- | :--- |
| Declaration | `class Name {}` | Creates a template for objects. |
| Private Field | `#property` | Limits access to the class body. |
| Inheritance | `extends Parent` | Borrows behavior from another class. |
| Static | `static method()` | Belongs to the class, not instances. |

### Code Implementation
```javascript
// 📘 Defining a class with encapsulation and inheritance
class Vehicle {
  #brand;
  constructor(brand) {
    this.#brand = brand;
  }
  get brand() { return this.#brand; } // 📘 Getter
}

class Car extends Vehicle {
  constructor(brand, model) {
    super(brand); // 📘 Call parent constructor
    this.model = model;
  }
}

const myCar = new Car("Ford", "Mustang");
console.log(myCar.brand); // ▶️ "Ford"
```

---

## 2. Arrays and Array Methods
Arrays are ordered, zero-indexed collections that can store heterogeneous data types. They are dynamic in size, allowing for the addition or removal of elements during execution.

*   **Key Properties:** The `length` property is dynamic and always one higher than the highest index.
*   **Methods:**
    *   `push()`: Adds elements to the end.
    *   `toString()`: Converts the array to a comma-separated string.
    *   `Array.isArray()`: The reliable way to check if a variable is an array (since `typeof` returns `"object"`).

---

## 3. Collections (Map and Set)
Beyond objects and arrays, JavaScript provides `Map` and `Set` for specialized data handling.

*   **Map:** A collection of keyed items that allows keys of **any type** (including objects). Unlike standard objects, `Map` preserves the insertion order of keys.
*   **Set:** A collection of **unique values**. It is highly optimized for uniqueness checks, performing significantly better than array-based searches (like `find` or `includes`).

```javascript
// 📘 Map and Set usage
const userMap = new Map();
userMap.set("id_1", { name: "Alice" });
console.log(userMap.size); // ▶️ 1

const uniqueIds = new Set([1, 2, 2, 3]);
console.log(uniqueIds.size); // ▶️ 3
```

---

## 4. Iterators and Iterables
Iterables are objects that implement the `Symbol.iterator` method. This allows them to be used in `for..of` loops.

*   **The Iterator Protocol:** The method must return an object with a `next()` function, which in turn returns `{ value, done }`.
*   **Array.from:** This utility converts "array-like" objects (objects with length and indices) or iterables into real arrays to enable the use of array methods.

---

## 5. Error Management
JavaScript utilizes `try...catch` blocks to handle exceptions gracefully, preventing program termination.

*   **Throwing Errors:** The `throw` statement allows for the creation of custom errors.
*   **The Error Object:** Built-in classes like `TypeError` and `ReferenceError` extend the base `Error` class, providing stack traces and messages.

---

## 6. Data Structures: Stack, Queue, Linked List, BST
The source context highlights several fundamental data structures for organized data manipulation.

### Linked List
A linear structure where elements (nodes) are not stored contiguously. Each node contains a value and a pointer to the next node.
*   **Advantages:** Dynamic size and efficient insertions/deletions.

### Binary Search Tree (BST)
A hierarchical structure where each node has at most two children.
*   **Ordering Property:** Left subtree values < Parent < Right subtree values.
*   **Performance:** Search, insertion, and deletion operate in $O(\log n)$ time when balanced.

---

## 7. Design Patterns
While specific code for patterns like Singleton or Factory is not detailed in the raw source, the context identifies them as essential components of "System Design" and "Advanced DSA" curricula. These patterns utilize the OOP features described in Section 1 to solve recurring architectural problems.

---

## 8. Integrated Example: Library Management System
This example integrates OOP, Collections, and Queue logic.

```javascript
class Book {
  constructor(title, author) {
    this.title = title;
    this.author = author;
  }
}

class Library {
  constructor() {
    this.catalog = new Map(); // 📘 Map for quick lookup
    this.waitlist = []; // 📘 Simple Queue
  }

  addBook(isbn, book) {
    this.catalog.set(isbn, book);
  }

  requestBook(user) {
    this.waitlist.push(user); // 📘 Enqueue
    return `${user} added to waitlist.`;
  }
}

const myLib = new Library();
myLib.addBook("123", new Book("JS Guide", "MDN"));
console.log(myLib.requestBook("UserA")); // ▶️ "UserA added to waitlist."
```

---

## 9. Trees
A tree is a non-linear, hierarchical data structure consisting of nodes connected by edges.

*   **Terminologies:**
    *   **Root:** Topmost node.
    *   **Leaf:** Node with no children.
    *   **Subtree:** A node and all its descendants.
*   **Traversals:**
    *   **DFS (Depth-First Search):** Includes Pre-Order, In-Order, and Post-Order.
    *   **BFS (Breadth-First Search):** Also known as Level-Order traversal.

### Practical Implementation: Product Category Tree
```javascript
class TreeNode {
  constructor(value) {
    this.value = value;
    this.children = []; // 📘 Multiple children for N-ary tree
  }
}

// 📘 Traversal Example: DFS Pre-Order
function preOrder(node) {
  if (!node) return;
  console.log(node.value);
  node.children.forEach(child => preOrder(child));
}

const electronics = new TreeNode("Electronics");
electronics.children.push(new TreeNode("Laptops"));
preOrder(electronics); // ▶️ "Electronics", "Laptops"
```

---

## 10. Graphs
A graph is a collection of vertices (nodes) and edges (connections). Unlike trees, graphs do not have a strict hierarchy and can contain cycles.

*   **Representations:**
    *   **Adjacency List:** A `Map` or array where each key is a vertex and the value is a list of its neighbors.
    *   **Adjacency Matrix:** A 2D boolean matrix representing connections.
*   **Search Algorithms:**
    *   **BFS:** Uses a **Queue** to explore neighbors level by level.
    *   **DFS:** Uses **Recursion** (or a stack) to explore as deep as possible.

### Practical Implementation: City Route System
```javascript
class Graph {
  constructor() {
    this.adjacencyList = new Map();
  }

  addVertex(city) {
    if (!this.adjacencyList.has(city)) {
      this.adjacencyList.set(city, []);
    }
  }

  addEdge(city1, city2) {
    this.adjacencyList.get(city1).push(city2); // 📘 Directed edge
  }

  bfs(start) {
    const queue = [start];
    const visited = new Set([start]);
    while (queue.length > 0) {
      const vertex = queue.shift();
      console.log(vertex);
      for (const neighbor of this.adjacencyList.get(vertex)) {
        if (!visited.has(neighbor)) {
          visited.add(neighbor);
          queue.push(neighbor);
        }
      }
    }
  }
}

const routes = new Graph();
routes.addVertex("Paris");
routes.addVertex("London");
routes.addEdge("Paris", "London");
routes.bfs("Paris"); // ▶️ "Paris", "London"
```