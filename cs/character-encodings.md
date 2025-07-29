# 🧵 Character Encodings

- [🧵 Character Encodings](#-character-encodings)
  - [👀 Fast Lookup](#-fast-lookup)
  - [💻 How Computers Read and Write Characters](#-how-computers-read-and-write-characters)
  - [🇺🇸 ASCII (7-bit, 1 byte)](#-ascii-7-bit-1-byte)
  - [📈 Extended ASCII (8-bit, 1 byte)](#-extended-ascii-8-bit-1-byte)
  - [📏 Variable Length Encodings](#-variable-length-encodings)
  - [🌍 Unicode](#-unicode)
  - [🔄 UTF](#-utf)
    - [🌐 UTF-8](#-utf-8)
    - [🔢 UTF-16 and UTF-32](#-utf-16-and-utf-32)

## 👀 Fast Lookup

**Key Definitions:**

- **Character Encoding**: A mapping system that converts characters to numbers and then to binary data (`character ↔ number ↔ binary`)
- **Unicode**: Universal standard that assigns unique code points to characters (e.g., 'A' = U+0041)
- **UTF**: Unicode Transformation Format - family of encodings that convert Unicode to binary

**Character Ranges:**

- **ASCII**: 0-127 (7 bits, English only)
- **Extended ASCII**: 0-255 (8 bits, limited additional characters)
- **Unicode**: U+0000 to U+10FFFF (supports all world languages)

**UTF Encoding Comparison:**

- **UTF-8**: Variable (1-4 bytes), ASCII compatible, web standard
- **UTF-16**: Variable (2-4 bytes), efficient for CJK languages
- **UTF-32**: Fixed (4 bytes), simple but space-inefficient

**Byte Recognition Patterns:**

- **UTF-8**: First byte bits indicate length (`0` = 1 byte, `110` = 2 bytes, `1110` = 3 bytes, `11110` = 4 bytes)
- **UTF-16**: Surrogate pairs (`0xD800-0xDBFF` = high surrogate, needs 4 bytes total)

**When to Use:**

- **UTF-8**: Web development, general text processing, mixed ASCII/international content
- **UTF-16**: Windows systems, Java strings, languages with many non-ASCII characters
- **UTF-32**: When you need simple character indexing and space isn't a concern

## 💻 How Computers Read and Write Characters

Humans read and write characters using letters, numbers, and symbols. But how do computers do it? Computers use **character encodings** to represent characters as numbers (binary data). So when you type a letter on your keyboard, the computer converts it into a specific binary code using a character encoding.

So basically, character encoding is a `character <-> number <-> binary` mapping.

For example, in ASCII encoding, the letter 'A' is represented by the number 65, which in binary is `01000001`. When you type 'A', the computer sees `01000001` and knows to display 'A' on the screen.

In this note, we will explore the different types of character encodings, how they **map characters to numbers**, and how they **convert those numbers to binary data**.

## 🇺🇸 ASCII (7-bit, 1 byte)

ASCII (American Standard Code for Information Interchange) is a character encoding standard that uses 7 bits (128 characters) to represent English letters, digits, and control characters. Each character is represented by a unique number from 0 to 127. For example:

- The letter 'A' is represented by the number **65**, which in binary is `01000001`.
- The letter 'B' is represented by the number **66**, which in binary is `01000010`.

> Type `man ascii` in your terminal to see the full ASCII table.
>
> But why 1byte is used for ASCII instead of 7 bits?
> It is because Computers were designed to handle data in chunks of 8 bits (1 byte) primarily for **hardware efficiency** and because **8 is a power of two** which means it can be easily processed by binary systems.
>
> The first 7 bits of the byte are used to represent the ASCII character, while the 8th bit is often used for parity or other purposes. This means that the first 128 characters (0-127) can be represented using just 7 bits, and the 8th bit is typically ignored or used for additional functionality.
>
> So when computer knows that the memory should be decoded as ASCII, it reads the 1byte, interprets the first 7 bits as a character. This is how computers read and write ASCII characters.

## 📈 Extended ASCII (8-bit, 1 byte)

Extended ASCII is an 8-bit character encoding standard that builds upon the original ASCII standard by using the 8th bit to represent an additional 128 characters (256 characters total). This allows for the inclusion of additional symbols, accented characters, and control codes. However, **Extended ASCII is not a single standardized encoding**; different systems may use different mappings for the additional characters. It is rarely used today so I won't go into details about it.

Single byte encodings are limited to 256 characters, which is sufficient for basic English text but not for many other languages. That's why variable-length encodings like UTF-8 were developed.

## 📏 Variable Length Encodings

## 🌍 Unicode

Before we dive into variable-length encodings, we need to understand what **Unicode** is. At the first section, I've mentioned that character encoding is a `character <-> number <-> binary` mapping. Unicode is the part of `character <-> number` mapping. For example, the letter 'A' is assigned the code point **U+0041**, which is 65 in decimal. Unicode assigns a single unique number called code point. It starts with `U+` prefix and is followed by a hexadecimal number. This code point is consistent and universal, meaning it applies to every character, regardless of the platform, program, or language. This means that 'A' will always be represented by U+0041 in Unicode, no matter where you use it.

Important part is that Unicode does not define how these characters are encoded in binary (`number <-> binary` mapping). That's where character encodings such as UTF-8 come into play.

## 🔄 UTF

UTF (Unicode Transformation Format) is a family of character encodings that represent Unicode characters in binary. The most common encodings in this family are UTF-8, UTF-16, and UTF-32. Each of these encodings has different characteristics in terms of how they represent characters and how much space they use.

### 🌐 UTF-8

UTF-8 is the most widely used character encoding on the web and is designed to be backward compatible with ASCII. It uses a variable-length encoding scheme, meaning that characters can be represented using 1 to 4 bytes, depending on the character's code point.

- **1 byte**: `U+0000` ~ `U+007F` (ASCII characters)
- **2 bytes**: `U+0080` ~ `U+07FF` (Latin, Cyrillic, Greek, etc.)
- **3 bytes**: `U+0800` ~ `U+FFFF` (Commonly used characters from various languages)
- **4 bytes**: `U+10000` ~ `U+10FFFF` (Supplementary characters, including emojis)

This means that UTF-8 can represent all Unicode characters while remaining efficient in terms of space for ASCII characters. For example, the letter 'A' in UTF-8 is still represented as `01000001`, just like in ASCII, but a character like '€' (Euro sign) would be represented as `11100010 10000010 10101100` in UTF-8, which is 3 bytes long.

Wait, how does UTF-8 know how many bytes to read for a character? It uses the **first few bits of the first byte** to indicate how many bytes are used for that character:

- If the first byte starts with `0`, it is a single-byte character (ASCII). (`0xxxxxxx`)
  - The first bit is `0`, and the next 7 bits represent the character.
- If it starts with `10`, it is a continuation byte for a multi-byte character.
- If it starts with `110`, it is a two-byte character.
  - (`110xxxxx 10xxxxxx`, **11 bits** will be used to represent the character)
- If it starts with `1110`, it is a three-byte character.
  - (`1110xxxx 10xxxxxx 10xxxxxx`, **16 bits** will be used to represent the character)
- If it starts with `11110`, it is a four-byte character.
  - (`11110xxx 10xxxxxx 10xxxxxx 10xxxxxx`, **21 bits** will be used to represent the character)

Let's take an example of the Euro sign '€':

- Unicode code point: `U+20AC`
  - Hexadecimal: `20AC`, Decimal: `8364`
  - In binary: `0010 0000 1010 1100` which needs 16 bits to represent.
- In UTF-8, it is represented as:
  - `11100010 10000010 10101100`
  - In first byte, first 4 bits `1110` indicate that this is a three-byte character, and the remaining bits `0010` represent the first part of the character.
  - The next two bytes start with `10`, indicating they are continuation bytes, and the remaining bits represent the rest of the character.

This variable-length encoding allows UTF-8 to efficiently represent a wide range of characters while maintaining compatibility with ASCII.

### 🔢 UTF-16 and UTF-32

**UTF-16** is another variable-length encoding that uses either 16 bits (2 bytes) or 32 bits (4 bytes) to represent characters:

- **2 bytes**: `U+0000` ~ `U+FFFF` (Basic Multilingual Plane)
- **4 bytes**: `U+10000` ~ `U+10FFFF` (Supplementary characters using surrogate pairs)

How does UTF-16 know whether to read 2 or 4 bytes? It uses **surrogate pairs** for characters that need 4 bytes:

- If the first 16-bit unit is in the range `0xD800` to `0xDBFF` (called a **high surrogate**), it means this is the start of a 4-byte character, and the next 16-bit unit will be a **low surrogate** (`0xDC00` to `0xDFFF`).
- If the first 16-bit unit is outside the surrogate range, it's a complete 2-byte character.

UTF-16 is more efficient than UTF-8 for languages that use characters outside the ASCII range (like Chinese, Japanese, Korean) since most of their characters can be represented in just 2 bytes. However, it's less efficient for ASCII text and is not backward compatible with ASCII.

**UTF-32** is a fixed-length encoding that uses exactly 32 bits (4 bytes) for every character. This means:

- **4 bytes**: All Unicode characters `U+0000` ~ `U+10FFFF`

UTF-32 is the simplest encoding to process since every character takes the same amount of space, making string operations like indexing straightforward. However, it's the most space-inefficient, using 4 bytes even for simple ASCII characters that could be represented in just 1 byte with UTF-8.
