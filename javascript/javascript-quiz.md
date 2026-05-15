# JavaScript Cuestionario

## Question 1
¿Cuál es la relación principal entre JavaScript y el estándar ECMAScript según el material proporcionado?

- [x] ECMAScript es la especificación del lenguaje y JavaScript es un dialecto o implementación de ese estándar.
- [ ] JavaScript es el estándar internacional y ECMAScript es la implementación exclusiva de Netscape.
- [ ] Son dos lenguajes de programación completamente diferentes sin relación técnica.
- [ ] ECMAScript es el nombre comercial de JavaScript para evitar problemas de marca con Oracle.

**Hint:** Considere cuál de los dos términos se refiere al documento de especificaciones técnicas y cuál al lenguaje que usamos.

## Question 2
¿Qué característica de ámbito introdujo la palabra clave 'let' en la versión ECMAScript 2015 (ES6)?

- [x] Ámbito de bloque (block scope).
- [ ] Ámbito global obligatorio.
- [ ] Ámbito de función exclusivamente (function scope).
- [ ] Ámbito de prototipo compartido.

**Hint:** Piense en cómo las llaves '{}' afectan a las variables declaradas con esta palabra clave en comparación con 'var'.

## Question 3
En el modelo de objetos de JavaScript, ¿cómo se maneja la herencia entre objetos?

- [x] A través de prototipos que actúan como planos compartidos.
- [ ] Mediante clases estáticas que no pueden modificarse en tiempo de ejecución.
- [ ] A través de la copia total de la memoria de un objeto padre a un hijo.
- [ ] Únicamente mediante la función 'Object.create(null)'.

**Hint:** Reflexione sobre el concepto de una cadena de búsqueda que vincula un objeto con sus ancestros.

## Question 4
El tipo primitivo 'BigInt', introducido en ECMAScript 2020, permite manipular enteros mayores a qué valor límite?

- [x] $Number.MAX\_SAFE\_INTEGER$ o $2^{53} - 1$.
- [ ] $2^{31} - 1$.
- [ ] $10^{100}$ (un gúgol).
- [ ] $Number.MIN\_VALUE$.

**Hint:** Se trata del valor máximo que un número de doble precisión IEEE 754 puede representar de forma exacta.

## Question 5
¿Qué diferencia fundamental existe entre el operador de unión nula ($??$) y el operador lógico OR ($||$)?

- [x] El operador $??$ solo devuelve el operando derecho si el izquierdo es 'null' o 'undefined'.
- [ ] El operador $??$ solo funciona con números enteros de tipo BigInt.
- [ ] El operador $||$ es más moderno y eficiente que el operador $??$.
- [ ] No existe diferencia; son sinónimos sintácticos en las versiones actuales.

**Hint:** Considere cómo reaccionaría cada operador si el valor de la izquierda fuera el número $0$.

## Question 6
Dentro del modelo de ejecución de JavaScript, ¿cuál es la función del 'Stack' (pila)?

- [x] Realizar el seguimiento de los contextos de ejecución y las llamadas a funciones.
- [ ] Almacenar objetos de gran tamaño de forma desestructurada.
- [ ] Gestionar la cola de tareas asíncronas pendientes del navegador.
- [ ] Compartir memoria de forma atómica entre múltiples hilos de ejecución.

**Hint:** Piense en la estructura LIFO (último en entrar, primero en salir) aplicada a las funciones.

## Question 7
¿Qué garantiza el principio de 'Run-to-completion' (ejecución hasta el final) en el bucle de eventos de JavaScript?

- [x] Que un trabajo actual se procesará completamente antes de que comience cualquier otro trabajo.
- [ ] Que el navegador nunca se bloqueará incluso si hay un bucle infinito.
- [ ] Que todas las promesas se resuelven en paralelo utilizando todos los núcleos del CPU.
- [ ] Que el código se compila a lenguaje máquina antes de ser ejecutado línea por línea.

**Hint:** Considere si una función puede ser pausada a la mitad para que otra función de una cola distinta se ejecute.

## Question 8
En el contexto de los agentes de JavaScript, ¿qué es un 'Realm' (reino)?

- [x] Un entorno que contiene un conjunto de objetos intrínsecos y un objeto global propio.
- [ ] Un tipo de servidor especializado para ejecutar JavaScript en el lado del servidor.
- [ ] Una extensión de seguridad que impide el acceso al DOM desde scripts externos.
- [ ] El nombre técnico de la memoria compartida entre Web Workers.

**Hint:** Piense en lo que sucede cuando tiene un 'iframe' y por qué '$instanceof Array$' podría fallar entre la ventana principal y el marco.

## Question 9
¿Cuál de las siguientes es una limitación importante de las funciones de flecha (arrow functions) introducidas en ES6?

- [x] No tienen su propio enlace a 'this'.
- [ ] No pueden aceptar más de dos parámetros de entrada.
- [ ] No permiten el uso de la palabra clave 'return'.
- [ ] Solo pueden ejecutarse dentro de bloques 'try...catch'.

**Hint:** Recuerde cómo estas funciones manejan el contexto del objeto que las invoca.

## Question 10
¿Qué permite hacer el operador de propagación o 'spread operator' ($...$) en JavaScript?

- [x] Expandir un iterable (como un array) en elementos individuales.
- [ ] Comprimir múltiples archivos JavaScript en un solo paquete de red.
- [ ] Convertir automáticamente una cadena de texto en un número entero.
- [ ] Cifrar datos sensibles antes de guardarlos en el 'localStorage'.

**Hint:** Imagine que quiere pasar todos los valores de una lista como si fueran parámetros separados en una función como '$Math.max()$'.
