# JavaScript Avanzado: Guía Completa con Ejemplos

Este documento proporciona una síntesis técnica y exhaustiva de las capacidades avanzadas de JavaScript, abarcando desde la programación orientada a objetos y estructuras de datos hasta patrones de diseño y gestión de colecciones. La información presentada se deriva exclusivamente del análisis de los materiales técnicos proporcionados.

## 1. Programación Orientada a Objetos

JavaScript utiliza un sistema basado en prototipos, pero las clases de ES6 proporcionan una abstracción más cercana a otros lenguajes orientados a objetos.

### Objetos Literales vs. Clases ES6
Los objetos literales son listas de pares clave-valor, ideales para almacenar datos simples. Las clases actúan como plantillas para crear múltiples objetos con las mismas propiedades y comportamientos.

### Constructor, Métodos, Static y Get/Set
*   **Constructor:** Un método especial (`constructor`) que se ejecuta automáticamente al crear una instancia para inicializar propiedades.
*   **Métodos:** Funciones compartidas entre todas las instancias a través del prototipo.
*   **Static:** Propiedades o métodos que pertenecen a la clase misma, no a las instancias (ej. `Date.now()`).
*   **Get/Set:** Accesores que permiten manipular propiedades como si fueran campos directos, permitiendo validación o encapsulamiento.

### Herencia y Campos Privados
La herencia se logra mediante `extends`. El método `super()` debe llamarse en el constructor de la clase derivada antes de acceder a `this`. Los campos privados se definen con el prefijo `#`, garantizando un encapsulamiento estricto ("hard private").

```javascript
class Vehiculo {
  #encendido = false; // Campo privado

  constructor(marca) {
    this.marca = marca;
  }

  get estado() {
    return this.#encendido ? "En marcha" : "Detenido";
  }

  arrancar() {
    this.#encendido = true;
  }
}

class Auto extends Vehiculo {
  constructor(marca, modelo) {
    super(marca);
    this.modelo = modelo;
  }

  info() {
    console.log(`${this.marca} ${this.modelo}: ${this.estado}`);
  }
}

const miAuto = new Auto("Toyota", "Corolla");
miAuto.arrancar();
miAuto.info(); // ▶️ [Toyota Corolla: En marcha]
console.log(miAuto.estado); // ▶️ [En marcha]
```

---

## 2. Arrays y sus Métodos

Los arrays en JavaScript son objetos especializados para colecciones ordenadas. Son dinámicos y pueden contener tipos de datos heterogéneos.

| Método | Descripción |
| :--- | :--- |
| **push / pop** | Añade/elimina elementos al final. |
| **shift / unshift** | Elimina/añade elementos al inicio. |
| **splice** | "Navaja suiza": inserta, elimina o reemplaza en cualquier posición. |
| **slice** | Crea una copia de una parte del array sin modificar el original. |
| **map** | Transforma cada elemento y devuelve un nuevo array. |
| **filter** | Devuelve un array con elementos que cumplen una condición. |
| **reduce** | Calcula un valor único basado en todo el array. |
| **find** | Devuelve el primer elemento que cumpla la condición. |
| **forEach** | Ejecuta una función para cada elemento (no devuelve nada). |
| **sort** | Ordena el array *in-place* (por defecto como strings). |
| **includes** | Verifica la existencia de un valor (maneja correctamente `NaN`). |

### Ejemplos Funcionales

```javascript
const numeros = [1, 2, 3, 4, 5];

// map: Cuadrados
const cuadrados = numeros.map(n => n * n);
console.log(cuadrados); // ▶️ [[1, 4, 9, 16, 25]]

// filter: Pares
const pares = numeros.filter(n => n % 2 === 0);
console.log(pares); // ▶️ [[2, 4]]

// reduce: Suma total
const suma = numeros.reduce((acc, n) => acc + n, 0);
console.log(suma); // ▶️ [15]

// find: Buscar el 3
const encontrado = numeros.find(n => n === 3);
console.log(encontrado); // ▶️ [3]

// push/pop
numeros.push(6);
console.log(numeros); // ▶️ [[1, 2, 3, 4, 5, 6]]
numeros.pop();
console.log(numeros); // ▶️ [[1, 2, 3, 4, 5]]

// sort: Numérico (usando función de comparación)
const desordenados = [1, 15, 2];
desordenados.sort((a, b) => a - b);
console.log(desordenados); // ▶️ [[1, 2, 15]]

// includes
console.log(numeros.includes(3)); // ▶️ [true]
```

---

## 3. Colecciones Keyed

### Map y Set
*   **Map:** Colección de pares clave/valor. A diferencia de los objetos, las claves pueden ser de cualquier tipo (objetos, funciones, primitivos) y mantienen el orden de inserción.
*   **Set:** Colección de valores únicos. Elimina duplicados automáticamente.

### WeakMap y WeakSet
*   **WeakMap:** Las claves deben ser objetos. No evita que los objetos sean recolectados por el *garbage collector* si no hay otras referencias. No es ejecutable (no se puede iterar).
*   **WeakSet:** Similar a Set pero solo para objetos y con referencias débiles.

```javascript
// Map
const inventario = new Map();
inventario.set("manzanas", 500);
console.log(inventario.get("manzanas")); // ▶️ [500]

// Set
const invitados = new Set(["Juan", "Maria", "Juan"]);
console.log(invitados.size); // ▶️ [2]
```

---

## 4. Iteradores y Generadores

### Symbol.iterator
Para que un objeto sea iterable (utilizable en `for...of`), debe implementar el método `Symbol.iterator`, el cual devuelve un objeto con un método `next()`.

### Generadores (`function*`)
Funciones que pueden pausar su ejecución con `yield` y reanudarla posteriormente.

```javascript
function* generadorId() {
  let id = 1;
  while (true) {
    yield id++;
  }
}

const gen = generadorId();
console.log(gen.next().value); // ▶️ [1]
console.log(gen.next().value); // ▶️ [2]
```

---

## 5. Gestión de Errores

JavaScript utiliza el bloque `try...catch...finally` para manejar excepciones. La sentencia `throw` permite lanzar errores personalizados o instancias de la clase `Error`.

```javascript
function validarEdad(edad) {
  if (edad < 18) throw new Error("Menor de edad");
  return true;
}

try {
  validarEdad(15);
} catch (err) {
  console.log(err.message); // ▶️ [Menor de edad]
} finally {
  console.log("Proceso terminado"); // ▶️ [Proceso terminado]
}
```

---

## 6. Estructuras de Datos

### Linked List (Lista Enlazada)
Estructura lineal donde cada nodo contiene un valor y una referencia al siguiente. Es dinámica y eficiente en inserciones/eliminaciones.

```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class LinkedList {
  constructor() {
    this.head = null;
  }

  append(value) {
    const newNode = new Node(value);
    if (!this.head) {
      this.head = newNode;
      return;
    }
    let current = this.head;
    while (current.next) current = current.next;
    current.next = newNode;
  }

  print() {
    let current = this.head;
    let res = "";
    while (current) {
      res += `${current.value}->`;
      current = current.next;
    }
    console.log(res + "null");
  }
}

const lista = new LinkedList();
lista.append(10);
lista.append(20);
lista.print(); // ▶️ [10->20->null]
```

### Stack y Queue
*   **Stack (Pila):** LIFO (Last-In, First-Out).
*   **Queue (Cola):** FIFO (First-In, First-Out).

---

## 7. Patrones de Diseño

1.  **Singleton:** Garantiza que una clase tenga una única instancia global.
2.  **Factory:** Proporciona una interfaz para crear objetos en una superclase, pero permite a las subclases alterar el tipo de objetos que se crearán.
3.  **Observer:** Define una dependencia uno-a-muchos; cuando el estado de un objeto cambia, todos sus dependientes son notificados automáticamente.
4.  **Module:** Encapsula lógica privada y expone solo lo necesario (utilizando clases con campos privados o cierres).

---

## 8. Ejemplo Integrador: Sistema de Biblioteca

Este sistema utiliza una clase `Library` que gestiona libros mediante un `Map`, una cola (`Queue`) para reservas y el patrón `Observer` para notificar a los usuarios.

```javascript
class Book {
  constructor(id, title) {
    this.id = id;
    this.title = title;
  }
}

class Library {
  _books = new Map();
  _reservations = []; // Queue simple
  _observers = []; // Pattern Observer

  addObserver(user) {
    this._observers.push(user);
  }

  notify(message) {
    this._observers.forEach(obs => obs.update(message));
  }

  addBook(book) {
    this._books.set(book.id, book);
    this.notify(`Nuevo libro disponible: ${book.title}`);
  }

  reserveBook(userId) {
    this._reservations.push(userId);
    console.log(`Usuario ${userId} en cola de reserva.`);
  }

  processReservation() {
    const nextUser = this._reservations.shift();
    if (nextUser) console.log(`Procesando reserva para: ${nextUser}`);
  }
}

class User {
  constructor(name) { this.name = name; }
  update(msg) { console.log(`${this.name} recibió: ${msg}`); }
}

// Ejecución
const myLib = new Library();
const user1 = new User("Ana");
myLib.addObserver(user1);

myLib.addBook(new Book(101, "JavaScript Avanzado")); 
// ▶️ [Ana recibió: Nuevo libro disponible: JavaScript Avanzado]

myLib.reserveBook("User_99"); 
// ▶️ [Usuario User_99 en cola de reserva.]

myLib.processReservation(); 
// ▶️ [Procesando reserva para: User_99]
```