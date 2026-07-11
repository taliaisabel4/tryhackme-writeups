# Software Basics

*This module explores how software represents and encodes data, and introduces the basics of programming and databases through Python, JavaScript, and SQL.*

[Data Representation](#-data-representation) · [Data Encoding](#-data-encoding) · [Python: Simple Demo](#-python-simple-demo) · [JavaScript: Simple Demo](#-javascript-simple-demo) · [Database SQL Basics](#-database-sql-basics)

## <img src="https://github.com/user-attachments/assets/5a583db9-a169-4b89-b4f6-412866bea4fe" width="50" height="50" align="middle" alt="Data Representation room icon"> Data Representation

*This room covers how computers represent data using bits and bytes, from colors and binary to hexadecimal and number conversions.*

### Representing Colors

If a computer were limited to 8 colors, it would only need to indicate which color is "switched on" and which is "switched off."

> It can use three digits of 1 and 0 to represent the states of red, green, and blue.

###### A way to represent a color in a palette of eight colors:

| **Color Representation** | **Representation Meaning** | **Color Name** |
| --- | --- | --- |
| `000` | All colors are off | Black |
| `001` | Only blue is on | Blue |
| `010` | Only green is on | Green |
| `100` | Only red is on | Red |
| `011` | Green and blue are on | Cyan |
| `101` | Red and blue are on | Magenta |
| `110` | Red and green are on | Yellow |
| `111` | All colors are on | White |

#### From 8 to 16,000,000

Being limited to eight colors is inconvenient, as we prefer millions of colors. One bit is enough to represent 2 states: on and off. We need 8 bits to express 256 states.

> A group of 8 bits is referred to as a **byte**.

#### Hexadecimal Representation

Hexadecimal representation makes it easy to combine 4 bits into a single character, a hexadecimal digit.

###### Hexadecimal to binary representation:

| **Hexadecimal Digit** | **Binary Representation** |
| --- | --- |
| `0` | `0000` |
| `1` | `0001` |
| `2` | `0010` |
| `3` | `0011` |
| `4` | `0100` |
| `5` | `0101` |
| `6` | `0110` |
| `7` | `0111` |
| `8` | `1000` |
| `9` | `1001` |
| `A` | `1010` |
| `B` | `1011` |
| `C` | `1100` |
| `D` | `1101` |
| `E` | `1110` |
| `F` | `1111` |

### Numbers: From Decimal to Hexadecimal

The binary (base-2) system can be expressed using the decimal (base-10) system.

> The key differences are that the binary system is limited to two digits, 0 and 1, and that everything is a power of 2.

###### Converting a decimal number to hexadecimal and binary:

| **Decimal Number** | **Hexadecimal Digit** | **Binary Representation** |
| --- | --- | --- |
| 0 | `0` | `0000` |
| 1 | `1` | `0001` |
| 2 | `2` | `0010` |
| 3 | `3` | `0011` |
| 4 | `4` | `0100` |
| 5 | `5` | `0101` |
| 6 | `6` | `0110` |
| 7 | `7` | `0111` |
| 8 | `8` | `1000` |
| 9 | `9` | `1001` |
| 10 | `A` | `1010` |
| 11 | `B` | `1011` |
| 12 | `C` | `1100` |
| 13 | `D` | `1101` |
| 14 | `E` | `1110` |
| 15 | `F` | `1111` |

### Key Takeaways

Computers represent all data as bits, the binary 1s and 0s that stand for on and off states. Combining bits expands what can be represented: three bits can encode eight colors, a byte of eight bits covers 256 values, and grouping enough bits allows millions of colors. Hexadecimal provides a compact way to write binary, with each hex digit standing for exactly four bits, which is why binary, decimal, and hexadecimal are used interchangeably to express the same underlying values.

## <img src="https://github.com/user-attachments/assets/67677f33-ae44-462a-b78c-96769626bc7d" width="50" height="50" align="middle" alt="Data Encoding room icon"> Data Encoding

*This room covers how text is encoded into numbers, from ASCII and the ISO/IEC 8859 standards to Unicode and the UTF encodings.*

### ASCII

The **American Standard Code for Information Interchange** (ASCII) uses numbers 0-127 to represent English letters, digits, punctuation, and some control characters. The original ASCII was limited to seven bits and acts as a small bilingual dictionary between text and numeric codes.

> ASCII is an early character encoding from 1963.

#### "TryHackMe" in ASCII

If you open a text file and write "TryHackMe" and save it as `file.txt`, the bit level will look like this: `01010100 01110010 01111001 01001000 01100001 01100011 01101011 01001101 01100101 00001010`.

When you open this file, the editor will read these bits and display the following characters: `T r y H a c k M e \n`; the \n is a new line that you get when you hit the `Enter` key.

#### European Languages

ASCII provided a way to encode the English alphabet. ASCII uses 7 bits, and with an eighth bit, we get 128 more characters to cover. The **ISO/IEC 8859 Series** (International Standards) created several standards, each standard covering a set of languages.

###### These standards are:

- **ISO-8859-1 (Latin-1)**: Covered Western European languages like German (ß, ü), French (é, ç), Spanish (ñ, ¿), Italian, Portuguese, Catalan, and Nordic languages (e.g., Icelandic ð/Ð).
- **ISO-8859-2 (Latin-2)**: Supported Central/Eastern European languages like Polish (ł, ń), Czech (č, ř), Hungarian (ő, ű), Croatian (đ), Romanian (ș, ț), and Slovak.

### Unicode

**Unicode** is a universal character encoding standard. It assigns unique code points to characters from all modern and historical writing systems worldwide. Unicode supports the interchange, processing, and display of text in diverse languages.

> Unicode 17.0 is currently the latest version of the Unicode Standard.

#### UTF-8, UTF-16, and UTF-32

**UTF-8**: A variable-width character encoding that represents each character using one to four bytes. It's backward-compatible with ASCII (the first 128 characters use a single byte) and is the dominant encoding on the web because it's space-efficient for Latin-based text.

**UTF-16**: A variable-width encoding that uses two or four bytes per character. It's more efficient than UTF-8 for text made up largely of characters outside the basic Latin range and is used internally by systems like Windows and Java.

**UTF-32**: A fixed-width encoding that uses exactly four bytes for every character. This makes character indexing simple and predictable, but it wastes space compared to the variable-width encodings, so it's used less often in practice.

### Key Takeaways

Character encoding maps text to numbers so computers can store and exchange it. ASCII was an early standard using seven bits to cover English letters, digits, and control characters, and the ISO/IEC 8859 series extended it with an eighth bit to support additional European languages. Unicode now provides a universal standard covering virtually all writing systems, and its UTF-8, UTF-16, and UTF-32 encodings offer different trade-offs between space efficiency and simplicity, with UTF-8 dominating the web.

## <img src="https://github.com/user-attachments/assets/c27b1a73-9710-481d-9e60-7abb4f84785a" width="50" height="50" align="middle" alt="Python: Simple Demo room icon"> Python: Simple Demo

*This room covers Python fundamentals such as variables, conditional statements, and iteration, by building a simple number-guessing game.*

### Variables

**Variables** store values the program tracks: `secret` (the number to guess), `tries` (attempt counter), and `guess` (the user's input).

The `random.randint(1, 20)` method returns a random integer within the given bounds. `tries` and `guess` both start at `0` - `guess` starts at 0 deliberately because a valid secret is 1-20, so it can never accidentally match. `print()` displays messages, `input()` captures text from the user, and `int()` converts that text into a number so it can be compared. Each guess increments the counter with `tries = tries + 1` (saved as `guess_v1.py`).

###### The game example is shown below:

```python
import random  # Gives us tools for picking random numbers

secret = random.randint(1, 20)  # a <= secret <= b
tries = 0
guess = 0  # Start with a value that cannot be the secret (since secret is 1..20)

print("I'm thinking of a number between 1 and 20")

text = input("Take a guess: ")  # input() returns text (a string)
guess = int(text)  # Convert the text to a number

tries = tries + 1  # Add 1 try
```

### Conditional Statements

**Conditional statements** compare the guess to the secret using `if` / `elif` / `else`.

Python checks `if` first; if false it tries each `elif` (Python's "else if"); if none are true it runs the final `else`. The four cases are out of range, too low, too high, or correct, using comparison operators (`<`, `>`) and the logical operator `or`. For example, with a secret of 10 and an input of 50, the first condition is true and it prints the "out of range" message (saved as `guess_v2.py`).

###### The game example is shown below:

```python
# Give a hint using if / elif / else.
if guess < 1 or guess > 20:
    print("That number is out of range. Try again.")
elif guess < secret:
    print("Too low, try again.")
elif guess > secret:
    print("Too high, try again.")
else:
    print("You got it in", tries, "tries!")
```

### Iterations

**Iterations** (loops) repeat a block of code as long as a condition holds, giving the user unlimited guesses.

The game uses a `while` loop written as `while guess != secret:`, where `!=` means "does not equal." Python checks the condition before each pass: if true it runs the indented block; if false the loop ends. Because `guess` starts at 0, the loop always runs at least once and stops only when the guess equals the secret (e.g., `10 != 10` is false, so it terminates).

###### Below is the complete final game, saved as `guess_v3.py`:

```python
import random  # Gives us tools for picking random numbers

# ----------------------------
# Guess the Number (Beginner Demo)
# ----------------------------
# The computer picks a secret number.
# The player keeps guessing until they find it.

secret = random.randint(1, 20)  # a <= secret <= b
tries = 0
guess = 0  # Start with a value that cannot be the secret (since secret is 1..20)

print("I'm thinking of a number between 1 and 20")

# Repeat until the user guesses the secret number.
while guess != secret:
    text = input("Take a guess: ")  # input() returns text (a string)
    guess = int(text)  # Convert the text to a number

    tries = tries + 1  # Add 1 try

    # Give a hint using if / elif / else.
    if guess < 1 or guess > 20:
        print("That number is out of range. Try again.")
    elif guess < secret:
        print("Too low, try again.")
    elif guess > secret:
        print("Too high, try again.")
    else:
        print("You got it in", tries, "tries!")
```

### Key Takeaways

The number-guessing game in Python introduces three core programming concepts. Variables store the values the program tracks, such as the secret number and the count of tries, while conditional statements (if, elif, else) compare the guess to the secret and decide which message to show. Iteration with a while loop repeats the guessing process until the correct answer is entered, turning the individual pieces into a complete, interactive program.

## <img src="https://github.com/user-attachments/assets/8241e0d5-1823-4642-a083-ec34ece97733" width="50" height="50" align="middle" alt="JavaScript: Simple Demo room icon"> JavaScript: Simple Demo

*This room covers JavaScript fundamentals such as variables, user input, conditional statements, and iteration, by building the same number-guessing game in JavaScript.*

### Variables

You use `let` to declare a variable, which holds a value that can change during the program, and `const` to declare a constant, whose value cannot change once set.

In the game, `tries` and `guess` are variables because they update as the user plays, while `secret` is a constant. The secret number is generated randomly by combining `Math.random()`, which returns a decimal between 0 (inclusive) and 1 (exclusive), with `* 20` to stretch that range, `Math.floor()` to round it down to a whole number, and `+ 1` to shift the result into the 1-20 range. Output is shown to the user with `console.log()`.

###### The game example is shown below:

```javascript
let tries = 0;
let guess = 0; // Initialized to a value that can't be the secret (1..20)

// Secret is constant and gets a new random value each run (1 <= secret <= 20)
const secret = Math.floor(Math.random() * (20)) + 1;

console.log("I'm thinking of a number between 1 and 20");
```

### Prompting the User for Input

The program asks the player to make a guess and captures what they type.

The line `rl.question()` waits for the user to enter a value and returns it as a string, which is stored in `text`. Because that input arrives as text rather than a number, it's passed through `parseInt(text, 10)`, which converts the string into an integer using base 10, and the result is saved in `guess`. This first draft (`guess_v1.js`) sets up the variables, picks the secret, prompts once, and counts the attempt, but it doesn't yet give the user any feedback about their guess.

###### The game examples is shown below:

```javascript
const text = await rl.question("Take a guess: ");
guess = parseInt(text, 10);
```

```javascript
import * as readline from "node:readline/promises";
import { stdin as input, stdout as output } from "node:process";

const rl = readline.createInterface({ input, output });

try {
  const secret = Math.floor(Math.random() * (20)) + 1; // 1 <= secret <= 20
  let tries = 0;
  let guess = 0; // Start with a value that cannot be the secret (since secret is 1..20)

  console.log("I'm thinking of a number between 1 and 20");

  const text = await rl.question("Take a guess: "); // Returns text (a string)
  guess = parseInt(text, 10); // Convert the text to a number

  tries = tries + 1; // Add 1 try
} finally {
  rl.close();
}
```

### Conditional Statements

THe program makes the game responsive by evaluating the guess and giving feedback.

Using an `if` / `else if` / `else` chain, the program first checks whether the guess is out of range (less than 1 or greater than 20, where `||` means "or"), then whether it is lower than the secret, then whether it is higher, and finally, if none of those are true, it concludes the guess must be correct. Because the conditions are mutually exclusive, chaining them with `else` avoids checking later conditions once an earlier one is satisfied. This draft (`guess_v2.js`) now tells the user whether they are out of range, too low, too high, or correct, but it still only runs once and gives them a single chance.

###### The game examples is shown below:

```javascript
// Give a hint using if / else if / else.
if (guess < 1 || guess > 20) {
  console.log("That number is out of range. Try again.");
} else if (guess < secret) {
  console.log("Too low, try again.");
} else if (guess > secret) {
  console.log("Too high, try again.");
} else {
  console.log("You got it in", tries, "tries!");
}
```

```javascript
import * as readline from "node:readline/promises";
import { stdin as input, stdout as output } from "node:process";

const rl = readline.createInterface({ input, output });

try {
  const secret = Math.floor(Math.random() * (20)) + 1; // 1 <= secret <= 20
  let tries = 0;
  let guess = 0;

  console.log("I'm thinking of a number between 1 and 20");

  const text = await rl.question("Take a guess: ");
  guess = parseInt(text, 10);

  tries = tries + 1;

  if (guess < 1 || guess > 20) {
    console.log("That number is out of range. Try again.");
  } else if (guess < secret) {
    console.log("Too low, try again.");
  } else if (guess > secret) {
    console.log("Too high, try again.");
  } else {
    console.log("You got it in", tries, "tries!");
  }
} finally {
  rl.close();
}
```

### Iterations

The final section makes the game repeatable so the user can keep guessing until they succeed.

This is done with a `while` loop, which repeats its body as long as its condition remains true. The condition `while (guess !== secret)` keeps prompting for new guesses while the guess is not equal to the secret, where `!==` means "not equal." Everything from the earlier tasks (prompting for input, converting it to a number, incrementing `tries`, and running the conditional feedback) now lives inside the loop, so the program continues until the correct number is entered.

###### Below is the complete final game, saved as guess_v3.js:

```javascript
// Repeat until the user guesses the secret number.
while (guess !== secret) {
  const text = await rl.question("Take a guess: ");
  guess = parseInt(text, 10);

tries = tries + 1;

  if (guess < 1 || guess > 20) {
    console.log("That number is out of range. Try again.");
  } else if (guess < secret) {
    console.log("Too low, try again.");
  } else if (guess > secret) {
    console.log("Too high, try again.");
  } else {
    console.log("You got it in", tries, "tries!");
  }
}
```

```javascript
import * as readline from "node:readline/promises";
import { stdin as input, stdout as output } from "node:process";

const rl = readline.createInterface({ input, output });

try {
  const secret = Math.floor(Math.random() * (20)) + 1; // 1 <= secret <= 20
  let tries = 0;
  let guess = 0;

  console.log("I'm thinking of a number between 1 and 20");

  // Repeat until the user guesses the secret number.
  while (guess !== secret) {
    const text = await rl.question("Take a guess: ");
    guess = parseInt(text, 10);

    tries = tries + 1;

    if (guess < 1 || guess > 20) {
      console.log("That number is out of range. Try again.");
    } else if (guess < secret) {
      console.log("Too low, try again.");
    } else if (guess > secret) {
      console.log("Too high, try again.");
    } else {
      console.log("You got it in", tries, "tries!");
    }
  }
} finally {
  rl.close();
}
```

### Key Takeaways

The number-guessing game in JavaScript introduces showing how the language expresses the same concepts. Variables are declared with let for values that change and const for those that do not, user input is captured as text and converted to a number with parseInt, and an if / else if / else chain provides feedback on each guess. A while loop then repeats the process until the guess matches the secret.

## <img src="https://github.com/user-attachments/assets/d3676ecc-be94-4622-94b5-cbd42e45263d" width="50" height="50" align="middle" alt="Database SQL Basics room icon"> Database SQL Basics

*This room covers the basics of databases and SQL, including tables, rows, and columns, and how to query data with SELECT, FROM, WHERE, and ORDER BY.*

### Understanding Tables, Rows, and Columns

**Database**: stores information in an organized way.
**Columns**: The titles at the top; each describes one type of information.
**Rows**: Goes across the table; each holds one complete record.

> Inside a database, data lives in **tables** (similar to spreadsheets).

**Café example:**

| **Concept** | **Example** |
|---|---|
| Columns | Order number, drink, price, time |
| Row     | One complete café order |

> Add an order → one row is added. Remove an order → only that row disappears; the rest stays intact.

The **Structured Query Language** (SQL) is the language used to ask questions (called **queries**) of a database. A **query** only displays requested data: it does not change the data itself.

### Writing Your First SQL Query

The practice uses two tables: `Orders (id, drink, price, time)` and `Menu (drink, price)`.

###### There are four core parts of the practice:

- `SELECT`
- `FROM`
- `WHERE`
- `ORDER BY`

#### Step 1: View Everything (`SELECT` and `FROM`)

`*` means "all columns"; `FROM` names the table.

###### Example shown below:

```sql
SELECT * FROM Orders;
```

#### Step 2: Show Specific Columns

List the columns you want after `SELECT`.

###### Example shown below:

```sql
SELECT drink, price FROM Orders;
```

#### Step 3: Filter Results (`WHERE`)

`WHERE` keeps only rows matching a condition.

###### Example shown below:

```sql
SELECT * FROM Orders WHERE drink = 'Coffee';
```

> To check which drink names exist, run `SELECT * FROM Menu;`.

#### Step 4: Sort Results (`ORDER BY`)

Sorts by a column; ascending by default. Add `DESC` for descending.

###### Example shown below:

```sql
SELECT * FROM Orders ORDER BY price;
SELECT * FROM Orders ORDER BY price DESC;
```

> The first line is lowest first, while the second line is highest first.

#### Step 5: Combine Filtering and Sorting

###### Example shown below:

```sql
SELECT * FROM Orders WHERE drink = 'Coffee' ORDER BY price DESC;
```

#### Quick Reference

| **Keyword** | **Purpose** |
|---------|---------|
| `SELECT` | Choose which columns to show (`*` = all) |
| `FROM` | Choose which table |
| `WHERE` | Filter rows by a condition |
| `ORDER BY` | Sort results (`DESC` = reverse) |

### Key Takeaways

Databases store information in tables made up of columns, which define the type of each piece of data, and rows, which hold individual records. SQL is the language used to query that data, and a query only displays information without changing what is stored. The four core clauses build on each other: `SELECT` and `FROM` choose the columns and table, `WHERE` filters rows by a condition, and `ORDER` BY sorts the results.
