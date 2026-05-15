# Programación Cuestionario

## Question 1
¿Cuál es la principal diferencia entre los métodos de array `splice` y `slice` en JavaScript?

- [x] `splice` modifica el array original, mientras que `slice` devuelve una nueva copia de una parte del array.
- [ ] `slice` puede eliminar elementos, mientras que `splice` solo puede copiar elementos de una posición a otra.
- [ ] Ambos métodos son idénticos y solo se diferencian en la sintaxis de sus argumentos de entrada.
- [ ] `splice` solo funciona con índices positivos, mientras que `slice` permite el uso de índices negativos.

**Hint:** Considera cuál de estos métodos actúa como una 'navaja suiza' que altera el contenido original.

## Question 2
En un Árbol Binario de Búsqueda (BST), ¿cuál es la propiedad fundamental que define la posición de los nodos?

- [x] Los valores del subárbol izquierdo deben ser estrictamente menores que el nodo actual, y los del derecho estrictamente mayores.
- [ ] Todos los nodos deben estar en el mismo nivel jerárquico para garantizar que el árbol esté balanceado.
- [ ] Cada nodo debe tener exactamente dos hijos, sin importar el valor que estos contengan.
- [ ] Los valores se insertan de forma secuencial de izquierda a derecha sin importar su magnitud numérica.

**Hint:** Piensa en cómo se comparan los valores de los hijos con respecto a su padre.

## Question 3
¿Cómo se define un campo privado dentro de una clase de JavaScript moderna?

- [x] Utilizando el símbolo `#` antes del nombre del identificador.
- [ ] Declarando la variable con la palabra clave `private` antes de su nombre.
- [ ] Encerrando el nombre de la propiedad entre guiones bajos, como en `_propiedad`.
- [ ] Definiendo la propiedad únicamente dentro del método constructor sin asignarla a `this`.

**Hint:** Recuerda el carácter especial que se integra directamente en el nombre de la propiedad.

## Question 4
¿Cuál es una ventaja clave de usar una lista enlazada en lugar de un array tradicional?

- [x] Permite inserciones y eliminaciones eficientes en cualquier posición sin necesidad de desplazar otros elementos.
- [ ] Ofrece acceso directo a cualquier elemento mediante un índice numérico en tiempo constante $O(1)$.
- [ ] Utiliza menos memoria total debido a que no requiere almacenar punteros o referencias adicionales.
- [ ] Garantiza que todos los datos se almacenen en bloques de memoria contiguos para mejorar la caché.

**Hint:** Piensa en el esfuerzo necesario para 'hacer espacio' en medio de una colección de datos.

## Question 5
¿Qué requisito debe cumplir un objeto para ser considerado un 'iterable' en JavaScript y poder usarse en un bucle `for..of`?

- [x] Debe implementar un método llamado `Symbol.iterator` que devuelva un objeto iterador.
- [ ] Debe tener una propiedad `length` y propiedades indexadas numéricamente.
- [ ] Debe ser una instancia directa de la clase `Array` o `String`.
- [ ] Debe carecer de métodos internos para asegurar que los datos sean inmutables durante el ciclo.

**Hint:** Busca el nombre del símbolo especial encargado de gestionar la secuencia de datos.

## Question 6
¿Qué sucede al intentar realizar una operación de `reduce` en un array vacío sin proporcionar un valor inicial?

- [x] Se produce un error de tipo (`TypeError`).
- [ ] El método devuelve automáticamente `undefined`.
- [ ] El acumulador se establece por defecto en $0$ y devuelve ese resultado.
- [ ] Se devuelve una copia del array vacío original.

**Hint:** Piensa en la seguridad del código cuando no hay datos disponibles para procesar.

## Question 7
En el contexto de los objetos en JavaScript, ¿qué significa que un objeto sea 'mutable'?

- [x] Que su contenido puede ser modificado después de su creación, incluso si la variable que lo referencia es constante.
- [ ] Que el objeto se convierte automáticamente en una cadena de texto al ser concatenado.
- [ ] Que el objeto no puede ser clonado ni copiado a otras variables.
- [ ] Que el tipo de dato del objeto cambia de forma dinámica entre número y cadena.

**Hint:** Diferencia entre la 'caja' (la variable) y lo que hay dentro de ella.

## Question 8
¿Cuál es una característica distintiva de un objeto `Set` en comparación con un `Array`?

- [x] Un `Set` garantiza que todos sus elementos sean únicos, eliminando duplicados automáticamente.
- [ ] Los elementos en un `Set` se ordenan alfabéticamente de forma automática.
- [ ] Un `Set` permite acceder a sus valores directamente mediante índices numéricos como `set[0]`.
- [ ] Un `Set` solo puede almacenar objetos y no valores primitivos.

**Hint:** Piensa en lo que sucede cuando intentas añadir el mismo valor dos veces.

## Question 9
¿A qué categoría pertenece el patrón de diseño 'Singleton' y cuál es su propósito?

- [x] Patrón creacional; asegura que una clase tenga una única instancia y proporciona un punto de acceso global.
- [ ] Patrón de comportamiento; define cómo se comunican los objetos mediante una jerarquía de mando.
- [ ] Patrón estructural; descompone objetos grandes en estructuras de árbol más manejables.
- [ ] Patrón creacional; permite clonar objetos existentes para evitar la sobrecarga del constructor.

**Hint:** El nombre del patrón sugiere la cantidad de instancias permitidas.

## Question 10
¿Cuál es la función del método `super()` dentro del constructor de una clase derivada?

- [x] Llama al constructor de la clase padre y es obligatorio antes de usar `this`.
- [ ] Sustituye todos los métodos de la clase actual por los de la clase base.
- [ ] Crea una instancia estática de la clase sin necesidad de usar `new`.
- [ ] Permite acceder a las propiedades privadas de la clase padre desde el hijo.

**Hint:** Considera el orden necesario para construir un objeto que hereda de otro.
