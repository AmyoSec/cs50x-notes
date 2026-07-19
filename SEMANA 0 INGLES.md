# CS50x Notes - Week 0

## Introduction and Course Philosophy

- **CS50** is Harvard's introductory course to the intellectual enterprises of computer science and the art of programming.
- The main goal **is not to teach a specific language**, but rather **to teach you how to think** computationally and solve problems.
- **Artificial intelligence** (AI) is transforming programming, but understanding the fundamentals remains essential.
- Using AI (like ChatGPT) to generate code is helpful, but **you must remain in control** and understand what you're doing.
- Practical example: in 10 lines of Python using OpenAI's API, a chatbot was built that answers questions with custom instructions.

## Representing Information

### The Binary System (Base 2)

- Computers only understand **two states**: **0 and 1** (off/on, no electricity/electricity).
- A **bit** (binary digit) is the smallest unit of information.
- A **byte** is **8 bits**.
- The **binary** system assigns weights to each position (1, 2, 4, 8, 16, …) from right to left.

| Decimal | Binary (4 bits) |
|---------|------------------|
| 0       | 0000             |
| 1       | 0001             |
| 2       | 0010             |
| 3       | 0011             |
| 4       | 0100             |
| 5       | 0101             |
| ...     | ...              |
| 15      | 1111             |

- With **n bits** we can represent **2ⁿ** values.
  - 8 bits → 256 values (0‑255).
  - 32 bits → about 4 billion (2³²).
  - 64 bits → astronomically large numbers.

### Representing Text

- **ASCII** (American Standard Code for Information Interchange): assigns a number to each character.
  - `'A'` = 65, `'B'` = 66, …, `'Z'` = 90.
  - `'a'` = 97, `'b'` = 98, … (difference of 32 from uppercase).
  - Example: `72 73 33` → `'H' 'I' '!'`.
- **Unicode**: extension of ASCII that can represent almost all characters in the world, including **emojis**.
  - Uses more bits (up to 32) to have millions of symbols.
  - The emoji 😂 (face with tears of joy) has a specific Unicode number (4,036,991,106 in decimal).

### Representing Colors and Images

- **RGB** system: each color is formed by combining **Red**, **Green**, and **Blue**.
- Each component uses one byte (0‑255).
  - `(0,0,0)` → black.
  - `(255,255,255)` → white.
  - `(255,0,0)` → pure red.
- An image is made of **pixels**; each pixel stores its color in 3 bytes (24 bits).
- A **video** is a sequence of images (frames) displayed rapidly (e.g., 30 fps).

### Representing Sound

- Sound can be represented by:
  - **Frequency** (pitch).
  - **Duration**.
  - **Volume** (amplitude).
- All of these are converted to numbers and, therefore, to bits.

---

## Algorithms

- An **algorithm** is a sequence of steps to solve a problem.
- Classic example: **finding a name in a phone book**.
  - Algorithm 1: start at the first page and go one by one → **linear** (O(n)).
  - Algorithm 2: go two by two → faster but can skip the page (needs correction).
  - Algorithm 3: open to the middle, decide if it's to the left or right, discard half, and repeat → **binary search** (O(log n)).
- **Efficiency**: graphical comparison of the three algorithms.
  - Linear: time ∝ number of pages (n).
  - Logarithmic: time grows very slowly even when doubling the problem size.

---

## Pseudocode

- It is a description in human language (or close to it) of an algorithm.
- It doesn't have strict syntax, but it helps with planning before coding.
- Example of the phone book algorithm in pseudocode:
1.Pick up the phone book

2.Open to the middle

3.Look at the page

4.If the person is on that page:
call the person
Else if the person is earlier:
open to the middle of the left half
go back to step 3
Else if the person is later:
open to the middle of the right half
go back to step 3
Else:
quit (person is not in the book)


- Key concepts:
  - **Functions**: actions or verbs (e.g., "open", "look").
  - **Conditionals**: decisions (if… else if…).
  - **Loops**: repeat actions (go back to step 3).
  - **Boolean expressions**: yes/no questions (e.g., "Is the person on the page?").

---

## Introduction to Scratch

**Scratch** is a visual block-based programming environment, developed by MIT. It allows learning programming concepts without worrying about syntax.

### Scratch Interface

- **Blocks palette**: categories (motion, looks, sound, events, control, sensing, operators, variables).
- **Scripts area**: where blocks are assembled.
- **Stage**: 2D world where objects (sprites) act.
- **Sprites**: characters or objects that can have their own programming.
- **Coordinates**: (x, y) with (0,0) in the center; x between -240 and 240, y between -180 and 180.

### Fundamental Blocks

- **Events**: `when green flag clicked` → starts the program.
- **Looks**: `say [text]` → displays a speech bubble.
- **Sensing**: `ask [text] and wait` → stores the answer in the `answer` variable.
- **Operators**: `join [string1] [string2]` → concatenates text.
- **Control**:
  - `repeat [n]` → loop with a fixed number of repetitions.
  - `forever` → infinite loop.
  - `wait [seconds]` → pause.
- **Variables**: you can create your own variables to store values (e.g., `score`).

### Example 1: "Hello World"

1. Drag `when green flag clicked`
2. Below it, place `say [Hello world]`
3. When the green flag is clicked, the cat says "Hello world".

### Example 2: Ask for name and greet

- Block `ask [What's your name?] and wait`
- The answer is stored in the `answer` variable (automatic).
- Use `join [Hello, ] [answer]` inside a `say` block.
- **Issue**: if only one `say` is used, the greeting appears too quickly; you can add a `wait` or concatenate in a single block.

### Example 3: Repeated meows

- With `forever` and `repeat` you can make the cat meow several times.
- Better to create a custom block `meow` that encapsulates the action.
- You can add an **argument** `n` to specify the number of times.
- This demonstrates the concept of **abstraction**: hiding internal details and reusing code.

### Example 4: Interaction with the mouse

- `forever` loop with condition `if touching mouse pointer?` → play sound.
- Without the loop, the program only checks once and won't detect subsequent movement.

---

## Decomposing Complex Programs

### "Oscar Time" Game

- **Version 0**: only changed the stage appearance and the sprite (a trash can).
- **Version 1**: the trash can reacts to the mouse by changing costume (lid open/closed) with an `if` inside a `forever`.
- **Version 2**: trash falls from the top and can be dragged; when it touches the trash can, it "disappears" and reappears at the top.
  - A block `go to x: (random) y: 180` is used to reposition.
  - Downward movement is achieved with `change y by -1` inside a loop.
- **Version 3**: a custom `go to top` block is created to avoid code duplication.
- **Version 4**: a `score` variable is added that increments each time the trash touches the trash can.

### "IB's hardest game"

- Control a sprite with the arrow keys.
- Collision detection with walls.
- Enemies move autonomously (bouncing or chasing the player).
- For an enemy to chase, use `point towards [sprite]` and `move [n] steps`.
- Difficulty is adjusted by changing the speed (number of steps).

---

## Abstraction and Code Design

- **Modularization**: divide the program into blocks or functions that perform specific tasks.
- **Reusability**: avoid copy-pasting; use loops and functions.
- **Best practices**:
  - Descriptive names for variables and blocks.
  - Keep code clean and organized.
  - Test each small part before integrating.

---

## Week 0 Conclusion

- We have seen the fundamentals of how computers represent and process information.
- Algorithmic thinking and the importance of efficiency have been introduced.
- We have practiced with Scratch, a visual environment that allows experimenting with all the basic programming concepts.
- The goal is that by the end of the course, you can transfer these ideas to textual languages like C, Python, etc.

---
