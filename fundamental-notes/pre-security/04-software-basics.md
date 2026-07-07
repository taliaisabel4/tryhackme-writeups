# Software Basics

*This module...*

[Data Representation](#data-representation) · [Data Encoding](#data-encoding) · [Python: Simple Demo](#python-simple-demo) · [JavaScript: Simple Demo](#javascript-simple-demo) · [Database SQL Basics](#database-sql-basics)

## Data Representation
<img width="384" height="384" alt="1773400279781-Room_Image-10" src="https://github.com/user-attachments/assets/5a583db9-a169-4b89-b4f6-412866bea4fe" />

*This room covers...*

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

Hexadecimal representation makes it easy to combine 4 bits into a single character, a hexadecimal digit

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

## Data Encoding
<img width="384" height="384" alt="1773400285735-Room_Image-13" src="https://github.com/user-attachments/assets/67677f33-ae44-462a-b78c-96769626bc7d" />

*This room covers...*

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

## Python: Simple Demo
<img width="384" height="384" alt="1773400291430-Room_Image-11" src="https://github.com/user-attachments/assets/c27b1a73-9710-481d-9e60-7abb4f84785a" />

#### Variables

Python offers the `random.randint()` method, which returns a random integer within the specified bounds.

#### Conditional Statements



#### Iterations



*This room covers...*

## JavaScript: Simple Demo
<img width="384" height="384" alt="1773400296115-Room_Image-12" src="https://github.com/user-attachments/assets/8241e0d5-1823-4642-a083-ec34ece97733" />

*This room covers...*

## Database SQL Basics
<img width="384" height="384" alt="1773400301430-Room_Image-14" src="https://github.com/user-attachments/assets/d3676ecc-be94-4622-94b5-cbd42e45263d" />

*This room covers...*
