# Programación Tarjetas

## Card 1

**Q:** ¿Cuál es la principal diferencia entre los métodos `slice` y `splice` en relación con el array original?

**A:** `splice` modifica el array original (es mutativo), mientras que `slice` devuelve un nuevo array sin alterar el original.

---

## Card 2

**Q:** En un Árbol de Búsqueda Binaria (BST), ¿qué condición deben cumplir los nodos del subárbol izquierdo respecto al nodo raíz?

**A:** Todos los nodos del subárbol izquierdo deben contener valores estrictamente menores que el valor del nodo raíz.

---

## Card 3

**Q:** El método de array que crea uno nuevo conteniendo únicamente los elementos que cumplen una condición específica es _____.

**A:** `filter`

---

## Card 4

**Q:** ¿Qué palabra clave se utiliza dentro del constructor de una clase derivada para invocar el constructor de su clase padre?

**A:** `super`

---

## Card 5

**Q:** ¿Cuál es la complejidad temporal promedio para buscar un elemento en un Árbol de Búsqueda Binaria (BST) equilibrado?

**A:** $O(\log n)$

---

## Card 6

**Q:** ¿Cómo se define un campo como 'privado' en una clase de JavaScript moderna?

**A:** Se debe prefijar el nombre del identificador con el símbolo `#`.

---

## Card 7

**Q:** Concepto: Patrón Singleton

**A:** Definición: Patrón creacional que garantiza que una clase tenga una sola instancia y proporciona un punto de acceso global a ella.

---

## Card 8

**Q:** ¿Qué método especial debe implementar un objeto para ser compatible con el bucle `for..of`?

**A:** `Symbol.iterator`

---

## Card 9

**Q:** ¿Cuál es la principal ventaja de una Lista Enlazada sobre un Array respecto a su tamaño?

**A:** Las listas enlazadas son dinámicas y pueden crecer o reducirse sin necesidad de definir un tamaño fijo inicial.

---

## Card 10

**Q:** ¿Qué valor devuelve el método `find` de un array si ningún elemento satisface la función de prueba?

**A:** `undefined`

---

## Card 11

**Q:** El método que procesa cada elemento de un array para acumularlo en un único valor de retorno se llama _____.

**A:** `reduce`

---

## Card 12

**Q:** ¿Por qué el método `sort()` puede ordenar números de forma contraintuitiva (ej. 1, 15, 2)?

**A:** Porque por defecto convierte los elementos en cadenas y realiza una ordenación lexicográfica.

---

## Card 13

**Q:** ¿Cuál es la utilidad principal del método `Array.from()`?

**A:** Transformar objetos iterables o similares a arrays (array-likes) en una instancia real de Array.

---

## Card 14

**Q:** ¿Cuál es el objetivo de los Patrones de Diseño Estructurales en el desarrollo de software?

**A:** Se enfocan en cómo se combinan clases y objetos para formar estructuras más grandes y complejas de forma eficiente.

---

## Card 15

**Q:** En la estructura de una Lista Enlazada, ¿cuáles son los dos componentes básicos de un 'Nodo'?

**A:** Un valor (los datos almacenados) y una referencia o puntero al siguiente nodo en la secuencia.

---

## Card 16

**Q:** ¿Cuál es la diferencia clave entre `Map` y `WeakMap` respecto a la gestión de memoria?

**A:** En `WeakMap`, las referencias a las claves (objetos) son débiles y no impiden que el recolector de basura las elimine.

---

## Card 17

**Q:** ¿Qué método de array devuelve el índice de la primera aparición de un elemento o -1 si no lo encuentra?

**A:** `indexOf`

---

## Card 18

**Q:** ¿Cuál es la función del método `constructor` dentro de una clase de JavaScript?

**A:** Es un método especial encargado de inicializar las propiedades de un objeto cuando se crea una nueva instancia.

---

## Card 19

**Q:** El patrón de diseño que notifica automáticamente a múltiples objetos dependientes sobre cualquier cambio de estado en un sujeto es el _____.

**A:** Patrón Observer

---

## Card 20

**Q:** ¿Por qué se prefiere el método `includes` sobre `indexOf` para verificar la existencia de un valor en un array?

**A:** Porque `includes` puede detectar correctamente el valor `NaN`, mientras que `indexOf` no puede.

---

## Card 21

**Q:** ¿Qué sucede si se intenta invocar un constructor de clase sin utilizar la palabra clave `new`?

**A:** JavaScript lanzará un error de tipo (`TypeError`).

---

## Card 22

**Q:** ¿Qué método estático de la clase `Array` se utiliza para determinar si el valor pasado es un array?

**A:** `Array.isArray()`

---

## Card 23

**Q:** ¿Cuál es la distinción técnica entre un objeto 'Iterable' y uno 'Array-like'?

**A:** Los iterables implementan `Symbol.iterator`, mientras que los array-likes tienen índices numéricos y propiedad `length`.

---

## Card 24

**Q:** ¿Qué patrón de diseño se utiliza para permitir que interfaces incompatibles colaboren entre sí?

**A:** Patrón Adapter

---

## Card 25

**Q:** ¿En qué orden se recorren los elementos de un objeto `Map` durante una iteración?

**A:** Se recorren siguiendo estrictamente el orden en que los elementos fueron insertados.

---

## Card 26

**Q:** ¿Qué acción realiza el método `splice` si el argumento `deleteCount` es 0?

**A:** Inserta nuevos elementos en la posición indicada sin eliminar ningún elemento existente.

---

## Card 27

**Q:** ¿Cuál es la complejidad temporal de búsqueda en un BST en el peor de los casos (árbol totalmente desequilibrado)?

**A:** $O(n)$

---

## Card 28

**Q:** ¿Qué palabra clave indica que una clase es hija de otra, heredando sus métodos y propiedades?

**A:** `extends`

---

## Card 29

**Q:** El método de array que ejecuta una función para cada elemento pero no devuelve ningún valor es _____.

**A:** `forEach`

---

## Card 30

**Q:** ¿Cuál es la diferencia de retorno entre `find` y `filter`?

**A:** `find` devuelve un único elemento (el primero hallado), mientras que `filter` devuelve un nuevo array con todos los hallazgos.

---

## Card 31

**Q:** ¿A qué hace referencia la palabra clave `this` dentro del ámbito del constructor de una clase?

**A:** Hace referencia a la instancia específica del objeto que se está creando en ese momento.

---

## Card 32

**Q:** ¿Qué método de cadenas (strings) se utiliza para separar un texto en un array según un delimitador?

**A:** `split`

---

## Card 33

**Q:** ¿Qué estructura debe tener el objeto devuelto por el método `next()` de un iterador?

**A:** Debe tener las propiedades `{done: Boolean, value: any}`.

---

## Card 34

**Q:** ¿Qué categoría de patrones de diseño se centra en la comunicación y asignación de responsabilidades entre objetos?

**A:** Patrones de Diseño de Comportamiento (Behavioral).

---

## Card 35

**Q:** ¿Qué ocurre si se intenta acceder a un miembro privado (`#`) de una clase desde un script externo?

**A:** Se genera un error de sintaxis que impide la ejecución del código.

---

## Card 36

**Q:** ¿Cuál es la función del parámetro `initial` en el método `reduce`?

**A:** Define el valor inicial del acumulador para la primera ejecución de la función de reducción.

---
