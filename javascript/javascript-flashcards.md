# JavaScript Tarjetas

## Card 1

**Q:** ¿Quién es el creador original del lenguaje JavaScript y en qué empresa lo desarrolló?

**A:** Brendan Eich, mientras trabajaba en Netscape Communications Corporation.

---

## Card 2

**Q:** ¿Cuál es la relación principal entre JavaScript y el estándar ECMAScript?

**A:** JavaScript es una implementación o dialecto basado en la especificación ECMAScript.

---

## Card 3

**Q:** ¿Qué nombre recibió JavaScript originalmente antes de ser renombrado para aprovechar la popularidad de Java?

**A:** Mocha (y posteriormente LiveScript).

---

## Card 4

**Q:** Nombre de la especificación técnica publicada por Ecma International que estandariza el lenguaje:

**A:** ECMA-262.

---

## Card 5

**Q:** ¿Cuál fue el motivo principal por el cual Microsoft desarrolló JScript en lugar de usar JavaScript?

**A:** Para evitar problemas legales relacionados con la marca registrada de Netscape y Sun Microsystems.

---

## Card 6

**Q:** ¿Cómo se define el sistema de tipos de JavaScript respecto al momento en que se vincula el tipo a un dato?

**A:** Tipado dinámico, donde el tipo está asociado al valor y no a la variable.

---

## Card 7

**Q:** ¿En qué consiste la característica de 'funciones de primera clase' en JavaScript?

**A:** En que las funciones son tratadas como objetos y pueden ser pasadas como argumentos o devueltas por otras funciones.

---

## Card 8

**Q:** ¿Qué paradigma de programación utiliza JavaScript para implementar la herencia entre objetos?

**A:** Programación basada en prototipos.

---

## Card 9

**Q:** ¿Qué diferencia existe entre el ámbito (scope) de una variable declarada con `var` y una declarada con `let`?

**A:** `var` tiene ámbito de función, mientras que `let` tiene ámbito de bloque.

---

## Card 10

**Q:** ¿Cuál es la función del operador de propagación o 'spread operator' (`...`) en arreglos?

**A:** Expande un arreglo o iterable en sus elementos individuales.

---

## Card 11

**Q:** ¿Para qué se utiliza la funcionalidad de desestructuración (destructuring) en objetos?

**A:** Para extraer propiedades de un objeto y asignarlas directamente a variables independientes.

---

## Card 12

**Q:** ¿Qué característica de las funciones de flecha (arrow functions) las hace inadecuadas para definir métodos de objetos?

**A:** No poseen su propio enlace al contexto `this`.

---

## Card 13

**Q:** ¿Cuál es el propósito del objeto `Promise` en JavaScript?

**A:** Representar la terminación o el fracaso eventual de una operación asíncrona.

---

## Card 14

**Q:** ¿Qué diferencia a un objeto `Map` de un objeto literal estándar en cuanto a sus claves?

**A:** En un `Map`, las claves pueden ser de cualquier tipo de dato, mientras que en objetos literales suelen ser cadenas o símbolos.

---

## Card 15

**Q:** ¿Qué garantiza el uso de un `Set` en comparación con un arreglo tradicional?

**A:** Que todos los valores almacenados sean únicos, ignorando duplicados.

---

## Card 16

**Q:** ¿Qué representa el tipo de dato primitivo `Symbol`?

**A:** Un identificador único e inmutable que evita colisiones de nombres en las propiedades de los objetos.

---

## Card 17

**Q:** ¿Cuál es la utilidad del operador de unión nula (`??`) introducido en ECMAScript 2020?

**A:** Devuelve el operando derecho si el izquierdo es `null` o `undefined`.

---

## Card 18

**Q:** ¿Cómo evita el encadenamiento opcional (`?.`) errores en tiempo de ejecución?

**A:** Permite acceder a propiedades anidadas devolviendo `undefined` en lugar de un error si una referencia es nula o indefinida.

---

## Card 19

**Q:** ¿Qué objeto global proporciona una forma estandarizada de acceder al objeto global en cualquier entorno de ejecución?

**A:** `globalThis`.

---

## Card 20

**Q:** ¿Para qué sirve el tipo primitivo `BigInt`?

**A:** Para representar y manipular enteros mayores que el límite de precisión de 64 bits ($2^{53} - 1$).

---

## Card 21

**Q:** En el modelo de ejecución de JavaScript, ¿cuál es la función de la pila de llamadas (call stack)?

**A:** Realizar el seguimiento de los contextos de ejecución y el flujo de control de las funciones (LIFO).

---

## Card 22

**Q:** ¿Qué componente del modelo de ejecución gestiona las tareas asíncronas y las coloca en la pila cuando está vacía?

**A:** El bucle de eventos (event loop).

---

## Card 23

**Q:** ¿Qué ocurre cuando se intenta acceder a una propiedad que no existe en un objeto específico?

**A:** JavaScript busca la propiedad de forma ascendente a través de la cadena de prototipos hasta llegar a `null`.

---

## Card 24

**Q:** ¿Cuál es la función de los bloques de inicialización estáticos (`static {}`) en las clases de ES2022?

**A:** Permiten ejecutar lógica de inicialización compleja para campos estáticos una sola vez al crear la clase.

---

## Card 25

**Q:** ¿Qué permite hacer el método `Object.hasOwn()`?

**A:** Comprobar si un objeto tiene una propiedad propia específica sin depender de la herencia del prototipo.

---

## Card 26

**Q:** ¿Qué característica de seguridad utiliza el navegador para ejecutar scripts en un entorno aislado?

**A:** Sandbox.

---

## Card 27

**Q:** ¿Qué restricción de seguridad impide que un script de un sitio acceda a datos de otro dominio diferente?

**A:** La política del mismo origen (Same-Origin Policy).

---

## Card 28

**Q:** ¿Qué ataque consiste en engañar al navegador para que realice peticiones no deseadas en nombre del usuario autenticado?

**A:** Falsificación de petición en sitios cruzados (CSRF).

---

## Card 29

**Q:** En el contexto de agentes y memoria compartida, ¿qué objeto permite la comunicación de memoria entre diferentes hilos?

**A:** `SharedArrayBuffer`.

---

## Card 30

**Q:** ¿Cuál es el propósito del objeto `Atomics` en aplicaciones multihilo?

**A:** Garantizar que las operaciones de memoria compartida sean predecibles y evitar condiciones de carrera.

---

## Card 31

**Q:** El principio por el cual una función 'recuerda' su entorno de variables incluso después de que la función externa haya terminado se llama _____.

**A:** Clausura (closure).

---

## Card 32

**Q:** ¿Qué método de `Array` se introdujo en ES6 para crear una instancia de arreglo a partir de un objeto iterable o similar a un arreglo?

**A:** `Array.from()`.

---

## Card 33

**Q:** ¿Qué diferencia hay entre `Array.prototype.find()` y `Array.prototype.findIndex()`?

**A:** `find` devuelve el valor del primer elemento que cumple la condición, mientras que `findIndex` devuelve su índice.

---

## Card 34

**Q:** ¿Qué hace el método `Math.trunc()`?

**A:** Elimina la parte fraccionaria de un número y devuelve su parte entera.

---

## Card 35

**Q:** ¿Cómo se define un 'agente' en la especificación de ejecución de JavaScript?

**A:** Es un ejecutor autónomo que posee su propio montón (heap), cola de trabajos y pila de contextos.

---

## Card 36

**Q:** Concepto: Realm

**A:** Definición: Conjunto de objetos intrínsecos, variables globales y entorno asociado a una pieza de código cargada.

---

## Card 37

**Q:** ¿Qué prioridad tienen las microtareas (como las promesas) frente a las macrotareas (como `setTimeout`) en el bucle de eventos?

**A:** Las microtareas tienen mayor prioridad y su cola se vacía completamente antes de procesar la siguiente macrotarea.

---

## Card 38

**Q:** ¿Qué técnica de optimización permite al motor descartar el contexto de ejecución actual si la llamada a la función es la última acción del llamador?

**A:** Llamada de cola adecuada (Proper Tail Call).

---

## Card 39

**Q:** ¿Qué sucede con una constante declarada con `const` si se intenta reasignar su valor?

**A:** Se produce un error de tipo (`TypeError`) porque el valor es inmutable tras la asignación inicial.

---

## Card 40

**Q:** ¿Para qué sirve el modificador `u` en las expresiones regulares?

**A:** Habilita el soporte completo para Unicode, tratando caracteres de 4 bytes como puntos de código únicos.

---
