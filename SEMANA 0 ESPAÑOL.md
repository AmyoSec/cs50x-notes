# Apuntes CS50x - Semana 0

## Introducción y filosofía del curso

- **CS50** es el curso introductorio de Harvard a la informática y al arte de la programación.
- El objetivo principal **no es enseñar un lenguaje concreto**, sino **enseñar a pensar** de forma computacional y a resolver problemas.
- La **inteligencia artificial** (IA) está transformando la programación, pero sigue siendo esencial dominar los fundamentos.
- Usar IA (como ChatGPT) para generar código es útil, pero **tú debes estar al mando** y comprender qué estás haciendo.
- Ejemplo práctico: en 10 líneas de Python usando la API de OpenAI, se construyó un chatbot que responde preguntas con instrucciones personalizadas.

## Representación de la información

### El sistema binario (base 2)

- Los ordenadores solo entienden **dos estados**: **0 y 1** (apagado/encendido, sin electricidad/con electricidad).
- Un **bit** (binary digit) es la unidad más pequeña de información.
- Un **byte** son **8 bits**.
- El sistema **binario** asigna pesos a cada posición (1, 2, 4, 8, 16, …) de derecha a izquierda.

| Decimal | Binario (4 bits) |
|---------|------------------|
| 0       | 0000             |
| 1       | 0001             |
| 2       | 0010             |
| 3       | 0011             |
| 4       | 0100             |
| 5       | 0101             |
| ...     | ...              |
| 15      | 1111             |

- Con **n bits** podemos representar **2ⁿ** valores.  
  - 8 bits → 256 valores (0‑255).
  - 32 bits → unos 4 mil millones (2³²).
  - 64 bits → números enormes.

### Representación de texto

- **ASCII** (American Standard Code for Information Interchange): asigna un número a cada carácter.
  - `'A'` = 65, `'B'` = 66, …, `'Z'` = 90.
  - `'a'` = 97, `'b'` = 98, … (diferencia de 32 con mayúsculas).
  - Ejemplo: `72 73 33` → `'H' 'I' '!'`.
- **Unicode**: extensión de ASCII que permite representar casi todos los caracteres del mundo, incluidos **emojis**.
  - Usa más bits (hasta 32) para tener millones de símbolos.
  - El emoji 😂 (cara con lágrimas de alegría) tiene un número Unicode específico (4 036 991 106 en decimal).

### Representación de colores e imágenes

- Sistema **RGB**: cada color se forma combinando **Rojo**, **Verde** y **Azul**.
- Cada componente usa un byte (0‑255).
  - `(0,0,0)` → negro.
  - `(255,255,255)` → blanco.
  - `(255,0,0)` → rojo puro.
- Una imagen está formada por **píxeles**; cada píxel guarda su color en 3 bytes (24 bits).
- Un **vídeo** es una secuencia de imágenes (fotogramas) que se muestran rápidamente (ej. 30 fps).

### Representación de sonido

- Se puede representar mediante:
  - **Frecuencia** (tono).
  - **Duración**.
  - **Volumen** (amplitud).
- Todo esto se convierte a números y, por tanto, a bits.

---

## Algoritmos

- Un **algoritmo** es una secuencia de pasos para resolver un problema.
- Ejemplo clásico: **buscar un nombre en una guía telefónica**.
  - Algoritmo 1: empezar por la primera página e ir de una en una → **lineal** (O(n)).
  - Algoritmo 2: ir de dos en dos → más rápido pero puede saltarse la página (se necesita corregir).
  - Algoritmo 3: abrir por la mitad, decidir si está a la izquierda o a la derecha, descartar la mitad y repetir → **búsqueda binaria** (O(log n)).
- **Eficiencia**: comparación gráfica de los tres algoritmos.
  - Lineal: tiempo ∝ número de páginas (n).
  - Logarítmico: tiempo crece muy lentamente incluso al duplicar el tamaño del problema.

---

## Pseudo código

- Es una descripción en lenguaje humano (o casi) de un algoritmo.
- No sigue una sintaxis estricta, pero ayuda a planificar antes de programar.
- Ejemplo del algoritmo de la guía telefónica en pseudocódigo:
1.Coger la guía telefónica

2.Abrir por la mitad

3.Mirar la página

4.Si la persona está en esa página:
llamar a la persona
Sino, si la persona está antes:
abrir por la mitad de la mitad izquierda
volver al paso 3
Sino, si la persona está después:
abrir por la mitad de la mitad derecha
volver al paso 3
Sino:
abandonar (no está en la guía)

- Conceptos clave:
  - **Funciones**: acciones o verbos (ej. "abrir", "mirar").
  - **Condicionales**: decisiones (si... sino si...).
  - **Bucles**: repetir acciones (volver al paso 3).
  - **Expresiones booleanas**: preguntas de sí/no (ej. "¿está la persona en la página?").

---

## Introducción a Scratch

**Scratch** es un entorno de programación visual por bloques, desarrollado por el MIT. Permite aprender conceptos de programación sin preocuparse por la sintaxis.

### Interfaz de Scratch

- **Paleta de bloques**: categorías (movimiento, apariencia, sonido, eventos, control, sensores, operadores, variables).
- **Área de programación**: donde se ensamblan los bloques.
- **Escenario**: mundo 2D donde actúan los objetos (sprites).
- **Sprites**: personajes u objetos que pueden tener programación propia.
- **Coordenadas**: (x, y) con (0,0) en el centro; x entre -240 y 240, y entre -180 y 180.

### Bloques fundamentales

- **Eventos**: `al presionar bandera verde` → inicia el programa.
- **Apariencia**: `decir [texto]` → muestra un globo de texto.
- **Sensores**: `preguntar [texto] y esperar` → guarda la respuesta en la variable `respuesta`.
- **Operadores**: `unir [cadena1] [cadena2]` → concatenar textos.
- **Control**:
  - `repetir [n]` → bucle con número fijo de repeticiones.
  - `por siempre` → bucle infinito.
  - `esperar [segundos]` → pausa.
- **Variables**: se pueden crear variables propias para almacenar valores (ej. `puntuación`).

### Ejemplo 1: "Hola mundo"

1. Arrastrar `al presionar bandera verde`
2. Debajo, colocar `decir [Hola mundo]`
3. Al hacer clic en la bandera verde, el gato dice "Hola mundo".

### Ejemplo 2: Preguntar nombre y saludar

- Bloque `preguntar [¿Cómo te llamas?] y esperar`
- Guardar la respuesta en la variable `respuesta` (automática).
- Usar `unir [Hola, ] [respuesta]` dentro de un `decir`.
- **Problema**: si se usa un solo `decir`, el saludo aparece muy rápido; se puede añadir un `esperar` o concatenar en un solo bloque.

### Ejemplo 3: Maullidos repetidos

- Con `por siempre` y `repetir` se puede hacer que el gato maúlle varias veces.
- Mejor crear un bloque personalizado `maullar` que encapsule la acción.
- Se puede añadir un **argumento** `n` para indicar el número de veces.
- Esto demuestra el concepto de **abstracción**: ocultar detalles internos y reutilizar.

### Ejemplo 4: Interacción con el ratón

- Bucle `por siempre` con condición `si ¿tocando el puntero del ratón?` → reproducir sonido.
- Sin el bucle, el programa solo comprueba una vez y no detecta el movimiento posterior.

---

## Descomposición de programas complejos

### Juego "Oscar Time"

- **Versión 0**: solo se cambió la apariencia del escenario y del sprite (un contenedor de basura).
- **Versión 1**: el contenedor reacciona al ratón cambiando de disfraz (tapa abierta/cerrada) con un `si` dentro de un `por siempre`.
- **Versión 2**: la basura cae desde arriba y se puede arrastrar; cuando toca el contenedor, "desaparece" y reaparece arriba.
  - Se usa un bloque `ir a x: (aleatorio) y: 180` para reposicionar.
  - El movimiento hacia abajo se logra con `cambiar y por -1` dentro de un bucle.
- **Versión 3**: se crea un bloque `ir a arriba` para evitar repetir código.
- **Versión 4**: se añade una variable `puntuación` que se incrementa cada vez que la basura toca el contenedor.

### Juego "IB's hardest game"

- Control de un sprite con las flechas del teclado.
- Detección de colisiones con paredes.
- Enemigos que se mueven autónomamente (rebotando o persiguiendo al jugador).
- Para que un enemigo persiga, se usa `apuntar hacia [sprite]` y `mover [n] pasos`.
- La dificultad se ajusta cambiando la velocidad (número de pasos).

---

## Abstracción y diseño de código

- **Modularización**: dividir el programa en bloques o funciones que realizan tareas específicas.
- **Reutilización**: evitar copiar y pegar; usar bucles y funciones.
- **Buenas prácticas**:
  - Nombres descriptivos para variables y bloques.
  - Mantener el código limpio y organizado.
  - Probar cada pequeña parte antes de integrarla.

---

## Conclusión de la semana 0

- Se han visto los fundamentos de cómo los ordenadores representan y procesan información.
- Se ha introducido el pensamiento algorítmico y la importancia de la eficiencia.
- Se ha practicado con Scratch, un entorno visual que permite experimentar con todos los conceptos básicos de programación.
- El objetivo es que, al final del curso, puedas trasladar estas ideas a lenguajes textuales como C, Python, etc.

---