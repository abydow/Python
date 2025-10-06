# 🐍 Python Regular Expressions (RegEx) - Complete Interactive Guide

[![Python RegEx](https://img.shields.io/badge/Python-Regular%20Expressions-blue?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
![Level](https://img.shields.io/badge/Level-Beginner%20to%20Advanced-orange?style=for-the-badge)

```ascii
╔══════════════════════════════════════════════════════════════════════════════╗
║                    🔍 PYTHON REGULAR EXPRESSIONS MASTERY 🔍                  ║
║                                                                              ║
║    ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐           ║
║    │ PATTERN │  │ SEARCH  │  │ MATCH   │  │ REPLACE │  │ SPLIT   │           ║
║    │ MAGIC   │  │ & FIND  │  │ & GRAB  │  │ & SWAP  │  │ & BREAK │           ║
║    └─────────┘  └─────────┘  └─────────┘  └─────────┘  └─────────┘           ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

## 📚 Table of Contents

- [🔥 What are Regular Expressions?](#-what-are-regular-expressions)
- [🚀 Getting Started with Python's `re` Module](#-getting-started-with-pythons-re-module)
- [🧩 Basic Pattern Building Blocks](#-basic-pattern-building-blocks)
- [🎯 Core `re` Module Functions](#-core-re-module-functions)
- [🔍 Metacharacters - The Special Symbols](#-metacharacters---the-special-symbols)
- [⚡ Quantifiers - Controlling Repetition](#-quantifiers---controlling-repetition)
- [📦 Character Classes and Sets](#-character-classes-and-sets)
- [🎪 Groups and Backreferences](#-groups-and-backreferences)
- [🚩 Flags and Modifiers](#-flags-and-modifiers)
- [💡 Advanced Patterns and Techniques](#-advanced-patterns-and-techniques)
- [🏆 Real-World Use Cases](#-real-world-use-cases)
- [⚠️ Best Practices and Common Pitfalls](#-best-practices-and-common-pitfalls)

---

## 🔥 What are Regular Expressions?

**Regular Expressions (RegEx)** are sequences of characters that define search patterns. Think of them as super-powered find-and-replace tools that can:

```ascii
┌─────────────────────────────────────────────────────────────────┐
│                       RegEx Power Grid                          │
├─────────────────────────────────────────────────────────────────┤
│  🔍 SEARCH     │  Find patterns in text                         │
│  ✅ VALIDATE   │  Check if text matches a format                │
│  🔄 REPLACE    │  Substitute matched patterns                   │
│  ✂️ SPLIT      │  Break text into pieces                        │
│  📊 EXTRACT    │  Pull specific data from text                  │
└─────────────────────────────────────────────────────────────────┘
```

### Real-World Examples:
- **Email validation**: `user@domain.com`
- **Phone number extraction**: `(123) 456-7890`
- **Date parsing**: `2024-01-15` or `01/15/2024`
- **Log file analysis**: Extract IPs, timestamps, error codes
- **Web scraping**: Extract URLs, links, data from HTML

---

## 🚀 Getting Started with Python's `re` Module

Python's built-in `re` module provides all regex functionality. Let's dive in!

```python
import re

# Your regex journey starts here! 🎯
```

### 📊 The re Module Architecture

```ascii
┌───────────────────────────────────────────────────────────────────────────┐
│                           Python re Module                                │
├─────────────────┬───────────────────┬───────────────────┬─────────────────┤
│    COMPILE      │      SEARCH       │      MATCH        │     MANIPULATE  │
│                 │                   │                   │                 │
│ re.compile()    │ re.search()       │ re.match()        │ re.sub()        │
│ ├─ Pattern      │ re.findall()      │ re.fullmatch()    │ re.subn()       │
│ │  Object       │ re.finditer()     │ ├─ Match Objects  │ re.split()      │
│ └─ Reusable     │ └─ Find All       │ └─ Groups         │ └─ Replace      │
└─────────────────┴───────────────────┴───────────────────┴─────────────────┘
```

### 🎪 Raw Strings - Your Regex Best Friend

**Always use raw strings (`r""`) for regex patterns!**

```python
# ❌ Without raw string - Escape character nightmare!
pattern_bad = "\\w+\\s\\d+"  # Double backslashes everywhere!

# ✅ With raw string - Clean and readable!
pattern_good = r"\w+\s\d+"  # Single backslashes work perfectly!

# Why? Let's see:
print("Normal string: ", "\\n")    # Output: \n (literal)
print("Normal string: ", "\n")     # Output: (newline)
print("Raw string: ", r"\n")       # Output: \n (literal)
```

---

## 🧩 Basic Pattern Building Blocks

### 🔤 Literal Characters

```ascii
┌────────────────────────────────────────────────────────────────┐
│                    Literal Matching                            │
├────────────────────────────────────────────────────────────────┤
│  Pattern: "cat"                                                │
│  Text:    "The cat sat on the mat"                             │
│           ╱───╲                                                │
│          ┌─────┐                                               │
│          │ cat │ ← MATCH!                                      │
│          └─────┘                                               │
└────────────────────────────────────────────────────────────────┘
```

```python
import re

text = "The cat sat on the mat"
result = re.search(r"cat", text)
print(f"Found: {result.group()}")  # Output: Found: cat
print(f"At position: {result.start()}-{result.end()}")  # Position: 4-7
```

### 🎯 Special Characters Overview

```ascii
┌─────────────────────────────────────────────────────────────────────────────┐
│                        Regex Special Characters                             │
├────────┬────────────────────────────────────────────────────────────────────┤
│   .    │ Any character (except newline)                                     │
│   ^    │ Start of string/line                                               │
│   $    │ End of string/line                                                 │
│   *    │ 0 or more repetitions                                              │
│   +    │ 1 or more repetitions                                              │
│   ?    │ 0 or 1 repetition (optional)                                       │
│  {...} │ Exact number of repetitions                                        │
│  [...] │ Character class (set)                                              │
│   \    │ Escape character                                                   │
│   |    │ OR operator                                                        │
│  (...) │ Grouping                                                           │
└────────┴────────────────────────────────────────────────────────────────────┘
```

---

## 🎯 Core `re` Module Functions

### 🔍 re.search() - Find First Match

```ascii
┌────────────────────────────────────────────────────────────────────────────┐
│                           re.search() Behavior                             │
├────────────────────────────────────────────────────────────────────────────┤
│  Text: "The quick brown fox jumps over the lazy dog"                       │
│  Pattern: r"o\w+"  (o followed by word characters)                         │
│                                                                            │
│  The quick brown fox jumps over the lazy dog                               │
│             ╱────╲                                                         │
│            ┌──────┐                                                        │
│            │ own  │ ← FIRST MATCH ONLY!                                    │
│            └──────┘                                                        │
│                                                                            │
│  Returns: Match object or None                                             │
└────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

text = "The quick brown fox jumps over the lazy dog"
pattern = r"o\w+"

match = re.search(pattern, text)
if match:
    print(f"Found: '{match.group()}'")      # Found: 'own'
    print(f"Position: {match.span()}")      # Position: (12, 15)
    print(f"Start: {match.start()}")        # Start: 12
    print(f"End: {match.end()}")            # End: 15
else:
    print("No match found")
```

### 🎪 re.findall() - Find All Matches

```ascii
┌────────────────────────────────────────────────────────────────────────────┐
│                          re.findall() Behavior                             │
├────────────────────────────────────────────────────────────────────────────┤
│  Text: "The quick brown fox jumps over the lazy dog"                       │
│  Pattern: r"o\w+"                                                          │
│                                                                            │
│  The quick brown fox jumps over the lazy dog                               │
│             ╱────╲              ╱────╲                                     │
│            ┌──────┐             ┌──────┐                                   │
│            │ own  │             │ over │ ← ALL MATCHES!                    │
│            └──────┘             └──────┘                                   │
│                                                                            │
│  Returns: ['own', 'over'] - List of strings                                │
└────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

text = "The quick brown fox jumps over the lazy dog"
pattern = r"o\w+"

matches = re.findall(pattern, text)
print(f"All matches: {matches}")  # All matches: ['own', 'over']

# More examples
text2 = "Contact: john@email.com, jane@domain.org, bob@test.net"
emails = re.findall(r"\w+@\w+\.\w+", text2)
print(f"Emails found: {emails}")  # ['john@email.com', 'jane@domain.org', 'bob@test.net']
```

### 🎯 re.match() - Match from Beginning

```ascii
┌─────────────────────────────────────────────────────────────────────────────┐
│                    re.match() vs re.search()                                │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  re.match() - Only checks START of string                                   │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │ ^Pattern must be here                                               │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
│                                                                             │
│  re.search() - Checks ENTIRE string                                         │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │ Pattern can be anywhere in the string                               │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
└─────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

text = "Hello, my name is John"

# re.match() - checks from beginning
match1 = re.match(r"Hello", text)
print(f"re.match 'Hello': {match1.group()}")    # ✅ Works: Hello

match2 = re.match(r"John", text)
print(f"re.match 'John': {match2}")             # ❌ None - John not at start

# re.search() - checks entire string
search1 = re.search(r"Hello", text)
print(f"re.search 'Hello': {search1.group()}")  # ✅ Works: Hello

search2 = re.search(r"John", text)
print(f"re.search 'John': {search2.group()}")   # ✅ Works: John
```

### 🔄 re.sub() - Search and Replace

```ascii
┌─────────────────────────────────────────────────────────────────────────────┐
│                           re.sub() Magic                                    │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Original: "The cat sat on the mat"                                         │
│  Pattern: r"cat"                                                            │
│  Replace: "dog"                                                             │
│                                                                             │
│  The cat sat on the mat                                                     │
│      ╱─╲                                                                    │
│     ┌───┐        REPLACE        ┌───┐                                       │
│     │cat│        ──────►        │dog│                                       │
│     └───┘                       └───┘                                       │
│                                                                             │
│  Result: "The dog sat on the mat"                                           │
└─────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

# Basic replacement
text = "The cat sat on the mat"
result = re.sub(r"cat", "dog", text)
print(result)  # The dog sat on the mat

# Replace all occurrences
text2 = "I like cats. Cats are great. Cats are cute."
result2 = re.sub(r"[Cc]ats?", "dogs", text2)  # cats or Cats, with optional s
print(result2)  # I like dogs. dogs are great. dogs are cute.

# Limit replacements
result3 = re.sub(r"[Cc]ats?", "dogs", text2, count=2)
print(result3)  # I like dogs. dogs are great. Cats are cute.
```

### ✂️ re.split() - Split by Pattern

```ascii
┌─────────────────────────────────────────────────────────────────────────────┐
│                          re.split() Power                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Text: "apple,banana;orange|grape"                                          │
│  Pattern: r"[,;|]"  (comma, semicolon, or pipe)                             │
│                                                                             │
│  apple , banana ; orange | grape                                            │
│        ▲         ▲        ▲                                                 │
│        │         │        │                                                 │
│     Split    Split    Split                                                 │
│                                                                             │
│  Result: ["apple", "banana", "orange", "grape"]                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

# Split by multiple delimiters
text = "apple,banana;orange|grape"
fruits = re.split(r"[,;|]", text)
print(fruits)  # ['apple', 'banana', 'orange', 'grape']

# Split by whitespace (multiple spaces/tabs)
text2 = "word1    word2\t\tword3   word4"
words = re.split(r"\s+", text2)
print(words)  # ['word1', 'word2', 'word3', 'word4']

# Split with limit
text3 = "a-b-c-d-e"
parts = re.split(r"-", text3, maxsplit=2)
print(parts)  # ['a', 'b', 'c-d-e']
```

---

## 🔍 Metacharacters - The Special Symbols

### 🎭 The Dot (.) - Any Character

```ascii
┌─────────────────────────────────────────────────────────────────────────────┐
│                        The Mighty Dot (.)                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Pattern: r"h.t"  (h + any character + t)                                   │
│                                                                             │
│  Text: "hat hit hot hut h@t h5t"                                            │
│         ╱─╲ ╱─╲ ╱─╲ ╱─╲ ╱─╲ ╱─╲                                             │
│        ┌───┬───┬───┬───┬───┬───┐                                            │
│        │hat│hit│hot│hut│h@t│h5t│ ← ALL MATCH!                               │
│        └───┴───┴───┴───┴───┴───┘                                            │
│                                                                             │
│  ⚠️  Doesn't match newline (\n) by default                                  │
└─────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

pattern = r"h.t"
text = "hat hit hot hut h@t h5t"

matches = re.findall(pattern, text)
print(f"Matches: {matches}")  # ['hat', 'hit', 'hot', 'hut', 'h@t', 'h5t']

# Dot doesn't match newline
text_with_newline = "hat\nhit"
matches2 = re.findall(r"t.h", text_with_newline)
print(f"Newline matches: {matches2}")  # [] - Empty!

# Use DOTALL flag to include newlines
matches3 = re.findall(r"t.h", text_with_newline, re.DOTALL)
print(f"With DOTALL: {matches3}")  # ['t\nh']
```

### ⚓ Anchors - ^ and $

```ascii
┌─────────────────────────────────────────────────────────────────────────────┐
│                           Anchors ^ and $                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ^ = Start of string/line                                                   │
│  $ = End of string/line                                                     │
│                                                                             │
│  Text: "Hello World"                                                        │
│                                                                             │
│  ^Hello ✅  │  Hello$ ❌  │  World$ ✅  │  ^World ❌                        │
│  ┌─────────┴─────────────┴─────────────┴──────────┐                         │
│  │ ^Hello World$  ← Matches entire string         │                         │
│  └─────────────────────────────────────────────────┘                        │
└─────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

text = "Hello World"

# Start anchor ^
print(re.search(r"^Hello", text))    # ✅ Match object
print(re.search(r"^World", text))    # ❌ None

# End anchor $
print(re.search(r"World$", text))    # ✅ Match object
print(re.search(r"Hello$", text))    # ❌ None

# Exact match (both anchors)
print(re.search(r"^Hello World$", text))  # ✅ Match object

# Multiline example
multiline_text = """First line
Second line
Third line"""

# Without MULTILINE flag
matches1 = re.findall(r"^Second", multiline_text)
print(f"Without MULTILINE: {matches1}")  # [] - Empty

# With MULTILINE flag
matches2 = re.findall(r"^Second", multiline_text, re.MULTILINE)
print(f"With MULTILINE: {matches2}")     # ['Second']
```

---

## ⚡ Quantifiers - Controlling Repetition

### 🎪 The Big Three: *, +, ?

```ascii
┌────────────────────────────────────────────────────────────────────────────┐
│                     Quantifier Visualization                               │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  *  = 0 or more    │  +  = 1 or more    │  ?  = 0 or 1 (optional)          │
│                    │                    │                                  │
│  ┌─ 0 times ──┐    │                    │  ┌─ 0 times ──┐                  │
│  │ 1 time     │    │  ┌─ 1 time ───┐    │  │ 1 time     │                  │
│  │ 2 times    │    │  │ 2 times    │    │  └────────────┘                  │
│  │ 3 times    │    │  │ 3 times    │    │                                  │
│  │ ...        │    │  │ ...        │    │                                  │
│  └────────────┘    │  └────────────┘    │                                  │
└────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

# * (0 or more)
text1 = "ab a ab abb abbb"
matches1 = re.findall(r"ab*", text1)
print(f"ab*: {matches1}")  # ['ab', 'a', 'ab', 'abb', 'abbb']

# + (1 or more)
matches2 = re.findall(r"ab+", text1)
print(f"ab+: {matches2}")  # ['ab', 'ab', 'abb', 'abbb'] - 'a' excluded!

# ? (0 or 1)
text2 = "color colour"
matches3 = re.findall(r"colou?r", text2)
print(f"colou?r: {matches3}")  # ['color', 'colour']
```

### 🎯 Precise Control: {n,m}

```ascii
┌─────────────────────────────────────────────────────────────────────────────┐
│                      Braces {} Quantifiers                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  {n}     = exactly n times                                                  │
│  {n,}    = n or more times                                                  │
│  {n,m}   = between n and m times                                            │
│                                                                             │
│  Example: \d{3,5} (3 to 5 digits)                                           │
│                                                                             │
│  Text: "12 123 1234 12345 123456"                                           │
│         ❌  ✅   ✅    ✅     ❌                                            │
│            ╱─╲  ╱──╲  ╱───╲                                                 │
│           123  1234  12345  ← Only these match!                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

text = "12 123 1234 12345 123456"

# Exactly 3 digits
exact_3 = re.findall(r"\b\d{3}\b", text)  # \b for word boundaries
print(f"Exactly 3: {exact_3}")  # ['123']

# 3 or more digits
three_or_more = re.findall(r"\b\d{3,}\b", text)
print(f"3 or more: {three_or_more}")  # ['123', '1234', '12345', '123456']

# Between 3 and 5 digits
between_3_5 = re.findall(r"\b\d{3,5}\b", text)
print(f"3 to 5: {between_3_5}")  # ['123', '1234', '12345']

# Phone number validation
phone_pattern = r"^\d{3}-\d{3}-\d{4}$"
phones = ["123-456-7890", "12-34-567", "123-456-78901"]
for phone in phones:
    if re.match(phone_pattern, phone):
        print(f"✅ {phone} is valid")
    else:
        print(f"❌ {phone} is invalid")
```

### 🍯 Greedy vs Lazy (Non-Greedy)

```ascii
┌─────────────────────────────────────────────────────────────────────────────┐
│                      Greedy vs Lazy Matching                                │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Greedy (* + {n,m})    = Match as MUCH as possible                          │
│  Lazy   (*? +? {n,m}?) = Match as LITTLE as possible                        │
│                                                                             │
│  Text: "<div>Hello</div><span>World</span>"                                 │
│                                                                             │
│  Greedy <.*>:                                                               │
│  ╭─────────────────────────────────────────────╮                            │
│  │ <div>Hello</div><span>World</span>         │ ← Entire string!            │
│  ╰─────────────────────────────────────────────╯                            │
│                                                                             │
│  Lazy <.*?>:                                                                |
|  ╭─────╮            ╭──────╮                                                │
│  │<div>│            │<span>│ ← Individual tags!                             │
│  ╰─────╯            ╰──────╯                                                │
└─────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

html = "<div>Hello</div><span>World</span>"

# Greedy matching - takes everything!
greedy = re.findall(r"<.*>", html)
print(f"Greedy: {greedy}")  # ['<div>Hello</div><span>World</span>']

# Lazy matching - stops at first opportunity
lazy = re.findall(r"<.*?>", html)
print(f"Lazy: {lazy}")      # ['<div>', '</div>', '<span>', '</span>']

# Practical example: Extract content between tags
content_greedy = re.findall(r"<div>(.*)</div>", html)
print(f"Content (greedy): {content_greedy}")  # ['Hello</div><span>World']

# Better approach using lazy
html2 = "<div>Hello</div>"
content_lazy = re.findall(r"<div>(.*?)</div>", html2)
print(f"Content (lazy): {content_lazy}")     # ['Hello']
```

---

## 📦 Character Classes and Sets

### 🎯 Predefined Character Classes

```ascii
┌─────────────────────────────────────────────────────────────────────────────┐
│                    Character Classes Cheat Sheet                            │
├────────┬────────────────────────────────────────────────────────────────────┤
│   \d   │ Digits [0-9]                    │   \D   │ Non-digits [^0-9]       │
│   \w   │ Word chars [a-zA-Z0-9_]         │   \W   │ Non-word chars          │
│   \s   │ Whitespace [ \t\n\r\f\v]        │   \S   │ Non-whitespace          │
│   \b   │ Word boundary                   │   \B   │ Non-word boundary       │
│   \A   │ Start of string                 │   \Z   │ End of string           │
└────────┴─────────────────────────────────┴────────┴─────────────────────────┘
```

```python
import re

text = "Hello World! 123 @#$"

# Digits
digits = re.findall(r"\d", text)
print(f"Digits: {digits}")  # ['1', '2', '3']

non_digits = re.findall(r"\D", text)
print(f"Non-digits: {non_digits}")  # ['H', 'e', 'l', 'l', 'o', ' ', ...]

# Word characters
words = re.findall(r"\w+", text)
print(f"Words: {words}")    # ['Hello', 'World', '123']

# Whitespace
spaces = re.findall(r"\s", text)
print(f"Spaces: {spaces}")  # [' ', ' ', ' ']

# Word boundaries
bounded_words = re.findall(r"\bWorld\b", text)
print(f"Bounded 'World': {bounded_words}")  # ['World']

# This won't match because 'orl' is not at word boundary
no_match = re.findall(r"\borl\b", text)
print(f"Bounded 'orl': {no_match}")         # []
```

### 🎨 Custom Character Sets [...]

```ascii
┌─────────────────────────────────────────────────────────────────────────────┐
│                        Character Sets [...]                                 │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  [abc]      │ Match any: a, b, or c                                         │
│  [a-z]      │ Match any lowercase letter                                    │
│  [A-Z]      │ Match any uppercase letter                                    │
│  [0-9]      │ Match any digit                                               │
│  [a-zA-Z]   │ Match any letter                                              │
│  [^abc]     │ Match anything EXCEPT a, b, or c                              │
│                                                                             │
│  Example: [aeiou] matches vowels                                            │
│  Text: "Hello World"                                                        │
│         ╱ ╱  ╱   ╱                                                          │
│        e o  o                                                               │
└─────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

text = "Hello World! 123 @#$"

# Vowels
vowels = re.findall(r"[aeiou]", text, re.IGNORECASE)
print(f"Vowels: {vowels}")  # ['e', 'o', 'o']

# Consonants (not vowels)
consonants = re.findall(r"[^aeiou\s\d\W]", text, re.IGNORECASE)
print(f"Consonants: {consonants}")  # ['H', 'l', 'l', 'W', 'r', 'l', 'd']

# Numbers and letters only
alphanumeric = re.findall(r"[a-zA-Z0-9]", text)
print(f"Alphanumeric: {alphanumeric}")  # ['H', 'e', 'l', 'l', 'o', ...]

# Hexadecimal digits
hex_text = "Color: #FF5733 and #1A2B3C"
hex_colors = re.findall(r"#[0-9A-Fa-f]{6}", hex_text)
print(f"Hex colors: {hex_colors}")  # ['#FF5733', '#1A2B3C']

# Special characters
specials = re.findall(r"[!@#$%^&*()]", text)
print(f"Special chars: {specials}")  # ['!', '@', '#', '$']
```

---

## 🎪 Groups and Backreferences

### 📦 Basic Grouping with ()

```ascii
┌─────────────────────────────────────────────────────────────────────────────┐
│                          Grouping with ()                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Pattern: r"(\w+)@(\w+)\.(\w+)"                                             │
│                                                                             │
│  Text: "john@example.com"                                                   │
│         ╱──╲ ╱─────╲ ╱─╲                                                    │
│        ┌────┬───────┬───┐                                                   │
│        │john│example│com│                                                   │
│        └────┴───────┴───┘                                                   │
│          ▲      ▲      ▲                                                    │
│       Group1  Group2 Group3                                                 │
│                                                                             │
│  Access: match.group(1), match.group(2), match.group(3)                     │
└─────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

# Email parsing with groups
email_pattern = r"(\w+)@(\w+)\.(\w+)"
email = "john@example.com"

match = re.search(email_pattern, email)
if match:
    print(f"Full match: {match.group()}")   # john@example.com
    print(f"Username: {match.group(1)}")    # john
    print(f"Domain: {match.group(2)}")      # example
    print(f"TLD: {match.group(3)}")         # com
    
    # Get all groups as tuple
    print(f"All groups: {match.groups()}")  # ('john', 'example', 'com')

# Phone number parsing
phone_pattern = r"(\d{3})-(\d{3})-(\d{4})"
phone = "123-456-7890"

phone_match = re.search(phone_pattern, phone)
if phone_match:
    area_code = phone_match.group(1)
    exchange = phone_match.group(2)
    number = phone_match.group(3)
    print(f"Area: {area_code}, Exchange: {exchange}, Number: {number}")
```

### 🏷️ Named Groups (?P<name>...)

```ascii
┌─────────────────────────────────────────────────────────────────────────────┐
│                           Named Groups                                      │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Pattern: r"(?P<username>\w+)@(?P<domain>\w+)\.(?P<tld>\w+)"                │
│                                                                             │
│  Benefits:                                                                  │
│  ✅ More readable code                                                      │
│  ✅ Self-documenting patterns                                               │
│  ✅ Less error-prone than numbers                                           │
│  ✅ Can still use numbers if needed                                         │
│                                                                             │
│  Access: match.group('username'), match.group('domain')                     │
└─────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

# Named groups for better readability
email_pattern = r"(?P<username>\w+)@(?P<domain>\w+)\.(?P<tld>\w+)"
email = "alice@github.com"

match = re.search(email_pattern, email)
if match:
    print(f"Username: {match.group('username')}")  # alice
    print(f"Domain: {match.group('domain')}")      # github
    print(f"TLD: {match.group('tld')}")            # com
    
    # Get as dictionary
    print(f"As dict: {match.groupdict()}")
    # {'username': 'alice', 'domain': 'github', 'tld': 'com'}

# Date parsing with named groups
date_pattern = r"(?P<year>\d{4})-(?P<month>\d{2})-(?P<day>\d{2})"
date = "2024-03-15"

date_match = re.search(date_pattern, date)
if date_match:
    year = date_match.group('year')
    month = date_match.group('month')
    day = date_match.group('day')
    print(f"Date: {month}/{day}/{year}")  # 03/15/2024
```

### 🔗 Backreferences - Referring to Groups

```ascii
┌─────────────────────────────────────────────────────────────────────────────┐
│                          Backreferences                                     │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Use \1, \2, \3... to refer back to captured groups                         │
│                                                                             │
│  Pattern: r"(\w+)\s+\1"  (word followed by same word)                       │
│                                                                             │
│  Text: "hello hello world world"                                            │
│         ╱─────────╲   ╱─────────╲                                           │
│        ┌───────────┐ ┌───────────┐                                          │
│        │hello hello│ │world world│                                          │
│        └───────────┘ └───────────┘                                          │
│          ▲       ▲                                                          │
│       Group1 = \1 (same as Group1)                                          │
└─────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

# Find repeated words
text = "This is is a test test with some some repeated words"
repeated_pattern = r"(\w+)\s+\1"

repeated_words = re.findall(repeated_pattern, text)
print(f"Repeated words: {repeated_words}")  # ['is', 'test', 'some']

# Find full matches (word + repetition)
repeated_matches = re.findall(r"(\w+\s+\1)", text)
print(f"Full matches: {repeated_matches}")  # ['is is', 'test test', 'some some']

# HTML tag matching
html = "<div>Content</div><span>More</span><p>Text</p>"
tag_pattern = r"<(\w+)>.*?</\1>"  # Opening tag matches closing tag

tags = re.findall(tag_pattern, html)
print(f"Matched tags: {tags}")  # ['div', 'span', 'p']

# Extract content between matching tags
content_pattern = r"<(\w+)>(.*?)</\1>"
content = re.findall(content_pattern, html)
print(f"Tag content: {content}")  # [('div', 'Content'), ('span', 'More'), ('p', 'Text')]
```

---

## 🚩 Flags and Modifiers

### 🎛️ Common Regex Flags

```ascii
┌─────────────────────────────────────────────────────────────────────────────┐
│                             Regex Flags                                     │
├─────────────┬───────────────────────────────────────────────────────────────┤
│ re.IGNORECASE │ Case-insensitive matching                                   │
│ re.I          │ (Short form)                                                │
├─────────────┼───────────────────────────────────────────────────────────────┤
│ re.MULTILINE  │ ^ and $ match line boundaries                               │
│ re.M          │ (Short form)                                                │
├─────────────┼───────────────────────────────────────────────────────────────┤
│ re.DOTALL     │ . matches newline too                                       │
│ re.S          │ (Short form)                                                │
├─────────────┼───────────────────────────────────────────────────────────────┤
│ re.VERBOSE    │ Allow comments and whitespace                               │
│ re.X          │ (Short form)                                                │
└─────────────┴───────────────────────────────────────────────────────────────┘
```

```python
import re

# IGNORECASE flag
text = "Hello WORLD world"

# Without flag - case sensitive
matches1 = re.findall(r"world", text)
print(f"Case sensitive: {matches1}")    # ['world']

# With IGNORECASE flag
matches2 = re.findall(r"world", text, re.IGNORECASE)
print(f"Case insensitive: {matches2}")  # ['WORLD', 'world']

# MULTILINE flag
multiline_text = """Start of first line
Start of second line
Not at start"""

# Without MULTILINE
matches3 = re.findall(r"^Start", multiline_text)
print(f"Without MULTILINE: {matches3}")  # ['Start'] - only first

# With MULTILINE
matches4 = re.findall(r"^Start", multiline_text, re.MULTILINE)
print(f"With MULTILINE: {matches4}")     # ['Start', 'Start'] - both lines

# DOTALL flag
text_with_newlines = "Hello\nWorld"

# Without DOTALL - . doesn't match \n
matches5 = re.findall(r"Hello.World", text_with_newlines)
print(f"Without DOTALL: {matches5}")     # []

# With DOTALL - . matches \n
matches6 = re.findall(r"Hello.World", text_with_newlines, re.DOTALL)
print(f"With DOTALL: {matches6}")        # ['Hello\nWorld']
```

### 🧹 VERBOSE Flag - Clean Patterns

```ascii
┌────────────────────────────────────────────────────────────────────────────┐
│                        VERBOSE Flag Magic                                  │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  Regular pattern: r"(\d{3})-(\d{3})-(\d{4})"                               │
│                                                                            │
│  VERBOSE pattern:                                                          │
│  r"""                                                                      │
│  (\d{3})      # Area code                                                  │
│  -            # Separator                                                  │
│  (\d{3})      # Exchange                                                   │
│  -            # Separator                                                  │
│  (\d{4})      # Number                                                     │
│  """                                                                       │
│                                                                            │
│  Benefits: Comments, whitespace, readability! 🎉                           │
└────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

# Complex email pattern - hard to read
email_pattern_complex = r"^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$"

# Same pattern with VERBOSE flag - much clearer!
email_pattern_verbose = r"""
^                    # Start of string
[a-zA-Z0-9._%+-]+    # Username: letters, numbers, dots, underscores, etc.
@                    # @ symbol
[a-zA-Z0-9.-]+       # Domain: letters, numbers, dots, hyphens
\.                   # Dot (escaped)
[a-zA-Z]{2,}         # TLD: at least 2 letters
$                    # End of string
"""

emails = ["user@example.com", "invalid-email", "test@domain.co.uk"]

for email in emails:
    if re.match(email_pattern_verbose, email, re.VERBOSE):
        print(f"✅ {email} is valid")
    else:
        print(f"❌ {email} is invalid")

# Phone number with verbose pattern
phone_pattern = r"""
(\d{3})              # Area code
-                    # Separator
(\d{3})              # Exchange
-                    # Separator
(\d{4})              # Number
"""

phone = "123-456-7890"
match = re.search(phone_pattern, phone, re.VERBOSE)
if match:
    print(f"Phone parsed: {match.groups()}")  # ('123', '456', '7890')
```

---

## 💡 Advanced Patterns and Techniques

### 🔍 Lookahead and Lookbehind

```ascii
┌────────────────────────────────────────────────────────────────────────────┐
│                        Lookahead & Lookbehind                              │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  Positive Lookahead  (?=...)  │ Must be followed by...                     │
│  Negative Lookahead  (?!...)  │ Must NOT be followed by...                 │
│  Positive Lookbehind (?<=...) │ Must be preceded by...                     │
│  Negative Lookbehind (?<!...) │ Must NOT be preceded by...                 │
│                                                                            │
│  Example: Find "cat" not followed by "s"                                   │
│  Pattern: r"cat(?!s)"                                                      │
│                                                                            │
│  Text: "cat cats category"                                                 │
│         ✅   ❌    ✅                                                      │
│        cat       cat (in category)                                         │
└────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

# Positive lookahead - password validation
text = "mypassword123 weakpass strongP@ss1"

# Password must contain digit (lookahead)
has_digit = r"\w*(?=\w*\d)\w*"
passwords_with_digit = re.findall(has_digit, text)
print(f"Passwords with digit: {passwords_with_digit}")

# Negative lookahead - find words not followed by 's'
text2 = "cat cats dog dogs bird birds"
not_plural = re.findall(r"\b\w+(?!s\b)", text2)
print(f"Non-plural words: {not_plural}")  # ['cat', 'dog', 'bird']

# Positive lookbehind - find numbers preceded by '$'
text3 = "Price: $19.99, Cost: 25.50, Tax: $3.75"
prices = re.findall(r"(?<=\$)\d+\.\d+", text3)
print(f"Prices: {prices}")  # ['19.99', '3.75']

# Negative lookbehind - find numbers NOT preceded by '$'
costs = re.findall(r"(?<!\$)\b\d+\.\d+", text3)
print(f"Non-prices: {costs}")  # ['25.50']

# Complex example: Extract domain without subdomain
emails = "user@mail.example.com, admin@example.com, test@sub.domain.org"
# Match domain that's not preceded by a dot (no subdomain)
domains = re.findall(r"@(?![\w.-]*\.)([a-zA-Z0-9.-]+\.[a-zA-Z]{2,})", emails)
print(f"Main domains: {domains}")
```

### 🔄 Non-Capturing Groups (?:...)

```ascii
┌────────────────────────────────────────────────────────────────────────────┐
│                      Non-Capturing Groups                                  │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  Regular Group: (...)     │ Captures content, creates backreference        │
│  Non-Capturing: (?:...)   │ Groups for precedence, no capture              │
│                                                                            │
│  Example: Match file extensions                                            │
│                                                                            │
│  Capturing:    r"(\w+)\.(jpg|png|gif)"                                     │
│  Groups: filename, extension                                               │
│                                                                            │
│  Non-Capturing: r"(\w+)\.(?:jpg|png|gif)"                                  │
│  Groups: filename only                                                     │
└────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

# With capturing groups
text = "photo.jpg image.png document.gif"

# This captures both filename and extension
with_capture = re.findall(r"(\w+)\.(jpg|png|gif)", text)
print(f"With capture: {with_capture}")  
# [('photo', 'jpg'), ('image', 'png'), ('document', 'gif')]

# Non-capturing group - only captures filename
without_capture = re.findall(r"(\w+)\.(?:jpg|png|gif)", text)
print(f"Without capture: {without_capture}")  
# ['photo', 'image', 'document']

# Useful for alternation without capturing
urls = "http://example.com https://secure.com ftp://files.com"

# Capture only the domain, not the protocol
domains = re.findall(r"(?:https?|ftp)://(\w+\.\w+)", urls)
print(f"Domains: {domains}")  # ['example.com', 'secure.com', 'files.com']

# Performance benefit - non-capturing groups are faster
# when you don't need the captured content
```

---

## 🏆 Real-World Use Cases

### 📧 Email Validation

```ascii
┌────────────────────────────────────────────────────────────────────────────┐
│                          Email Validation                                  │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  Basic: user@domain.com                                                    │
│  ┌──────────┬─┬─────────┬─┬─────┐                                          │
│  │ Username │@│ Domain  │.│ TLD │                                          │
│  └──────────┴─┴─────────┴─┴─────┘                                          │
│                                                                            │
│  Complex cases:                                                            │
│  • user.name+tag@sub.domain.co.uk                                          │
│  • special_chars%123@domain-name.com                                       │
│  • numbers123@domain123.org                                                │
└────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

def validate_email(email):
    """Comprehensive email validation"""
    pattern = r"""
    ^                           # Start of string
    [a-zA-Z0-9._%+-]+           # Username part
    @                           # @ symbol
    [a-zA-Z0-9.-]+              # Domain name
    \.[a-zA-Z]{2,}             # TLD (at least 2 chars)
    $                           # End of string
    """
    return re.match(pattern, email, re.VERBOSE) is not None

def extract_emails_from_text(text):
    """Extract all emails from text"""
    pattern = r'\b[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}\b'
    return re.findall(pattern, text)

# Test emails
test_emails = [
    "user@example.com",          # ✅ Valid
    "test.email@domain.co.uk",   # ✅ Valid
    "invalid.email",             # ❌ No @ or domain
    "@domain.com",               # ❌ No username
    "user@.com",                 # ❌ No domain
    "user@domain",               # ❌ No TLD
]

for email in test_emails:
    status = "✅ Valid" if validate_email(email) else "❌ Invalid"
    print(f"{status}: {email}")

# Extract emails from text
sample_text = """
Contact us at support@company.com for help.
Sales inquiries: sales@company.com
CEO email: ceo@company.co.uk
Invalid: not.an.email
"""

found_emails = extract_emails_from_text(sample_text)
print(f"\nFound emails: {found_emails}")
```

### 📱 Phone Number Processing

```python
import re

def normalize_phone(phone):
    """Convert phone to standard format"""
    # Remove all non-digits
    digits = re.sub(r'\D', '', phone)
    
    # Handle different formats
    if len(digits) == 10:
        # Format: (123) 456-7890
        return re.sub(r'(\d{3})(\d{3})(\d{4})', r'(\1) \2-\3', digits)
    elif len(digits) == 11 and digits[0] == '1':
        # Remove country code and format
        return normalize_phone(digits[1:])
    else:
        return "Invalid phone number"

def extract_phones(text):
    """Extract all phone numbers from text"""
    patterns = [
        r'\b\d{3}-\d{3}-\d{4}\b',           # 123-456-7890
        r'\b\(\d{3}\)\s*\d{3}-\d{4}\b',     # (123) 456-7890
        r'\b\d{3}\.\d{3}\.\d{4}\b',         # 123.456.7890
        r'\b\d{10}\b',                       # 1234567890
    ]
    
    phones = []
    for pattern in patterns:
        phones.extend(re.findall(pattern, text))
    
    return phones

# Test phone numbers
test_phones = [
    "123-456-7890",
    "(123) 456-7890",
    "123.456.7890",
    "1234567890",
    "+1 123 456 7890",
    "123 456 7890"
]

for phone in test_phones:
    normalized = normalize_phone(phone)
    print(f"{phone:15} → {normalized}")

# Extract from text
text = """
Call us at 123-456-7890 or (987) 654-3210
Fax: 555.123.4567
Mobile: 9876543210
Invalid: 123-45-678
"""

found_phones = extract_phones(text)
print(f"\nFound phones: {found_phones}")
```

### 🌐 URL Processing

```python
import re

def validate_url(url):
    """Validate URL format"""
    pattern = r"""
    ^                                   # Start
    https?://                           # Protocol
    (?:www\.)?                          # Optional www
    [a-zA-Z0-9.-]+                      # Domain
    \.[a-zA-Z]{2,}                     # TLD
    (?:/[^\s]*)?                        # Optional path
    $                                   # End
    """
    return re.match(pattern, url, re.VERBOSE) is not None

def extract_domains(text):
    """Extract unique domains from text"""
    pattern = r'https?://(?:www\.)?([a-zA-Z0-9.-]+\.[a-zA-Z]{2,})'
    domains = re.findall(pattern, text)
    return list(set(domains))  # Remove duplicates

def clean_url(url):
    """Clean and standardize URL"""
    # Remove tracking parameters
    cleaned = re.sub(r'\?utm_[^&\s]*(?:&[^&\s]*)*', '', url)
    
    # Remove trailing slash if present
    cleaned = re.sub(r'/$', '', cleaned)
    
    return cleaned

# Test URLs
test_urls = [
    "https://www.example.com",
    "http://domain.org/path",
    "https://sub.domain.co.uk/path/file.html",
    "invalid-url",
    "ftp://files.com"  # Different protocol
]

for url in test_urls:
    status = "✅ Valid" if validate_url(url) else "❌ Invalid"
    print(f"{status}: {url}")

# Extract domains
text = """
Visit https://www.google.com for search
Check out http://github.com/user/repo
News at https://news.bbc.co.uk
Same site: https://www.google.com/search
"""

domains = extract_domains(text)
print(f"\nUnique domains: {domains}")

# Clean URLs
urls_to_clean = [
    "https://example.com/?utm_source=google&utm_medium=cpc",
    "https://shop.com/product/?utm_campaign=sale",
    "https://site.com/page/"
]

for url in urls_to_clean:
    cleaned = clean_url(url)
    print(f"Original: {url}")
    print(f"Cleaned:  {cleaned}\n")
```

### 📊 Log File Analysis

```python
import re
from collections import Counter
from datetime import datetime

def parse_apache_log(log_line):
    """Parse Apache access log line"""
    pattern = r'''
    (\d+\.\d+\.\d+\.\d+)              # IP address
    \s-\s-\s                          # Separators
    \[([^\]]+)\]                      # Timestamp
    \s"                               # Start of request
    (\w+)\s                           # HTTP method
    ([^\s]+)\s                        # URL path
    HTTP/[\d\.]+"\s                   # HTTP version
    (\d+)\s                           # Status code
    (\d+)                             # Response size
    '''
    
    match = re.match(pattern, log_line, re.VERBOSE)
    if match:
        ip, timestamp, method, path, status, size = match.groups()
        return {
            'ip': ip,
            'timestamp': timestamp,
            'method': method,
            'path': path,
            'status': int(status),
            'size': int(size)
        }
    return None

def analyze_log_file(log_content):
    """Analyze Apache log file content"""
    lines = log_content.strip().split('\n')
    parsed_logs = []
    
    for line in lines:
        parsed = parse_apache_log(line)
        if parsed:
            parsed_logs.append(parsed)
    
    if not parsed_logs:
        return {}
    
    # Analysis
    ips = [log['ip'] for log in parsed_logs]
    statuses = [log['status'] for log in parsed_logs]
    paths = [log['path'] for log in parsed_logs]
    
    return {
        'total_requests': len(parsed_logs),
        'unique_ips': len(set(ips)),
        'top_ips': Counter(ips).most_common(3),
        'status_codes': Counter(statuses),
        'top_pages': Counter(paths).most_common(5),
        'error_rate': sum(1 for s in statuses if s >= 400) / len(statuses) * 100
    }

# Sample log data
sample_log = '''
192.168.1.100 - - [10/Mar/2024:10:15:30 +0000] "GET /index.html HTTP/1.1" 200 1234
192.168.1.101 - - [10/Mar/2024:10:16:45 +0000] "POST /api/login HTTP/1.1" 200 567
192.168.1.100 - - [10/Mar/2024:10:17:12 +0000] "GET /about.html HTTP/1.1" 404 89
192.168.1.102 - - [10/Mar/2024:10:18:33 +0000] "GET /index.html HTTP/1.1" 200 1234
192.168.1.101 - - [10/Mar/2024:10:19:45 +0000] "GET /contact.html HTTP/1.1" 500 234
'''

analysis = analyze_log_file(sample_log)
print("📊 Log Analysis Results:")
print(f"Total requests: {analysis['total_requests']}")
print(f"Unique IPs: {analysis['unique_ips']}")
print(f"Error rate: {analysis['error_rate']:.1f}%")
print(f"Top IPs: {analysis['top_ips']}")
print(f"Status codes: {dict(analysis['status_codes'])}")
print(f"Top pages: {analysis['top_pages']}")
```

---

## ⚠️ Best Practices and Common Pitfalls

### ✅ Do's and ❌ Don'ts

```ascii
┌─────────────────────────────────────────────────────────────────────────────┐
│                          Regex Best Practices                               │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ✅ DO                                 │  ❌ DON'T                          │
│  ───────────────────────────────────────────────────────────────────────────│
│  Use raw strings r""                  │  Forget raw strings                 │
│  Compile patterns for reuse           │  Re-compile in loops                │
│  Use meaningful group names           │  Rely only on numbers               │
│  Test with edge cases                 │  Assume patterns always work        │
│  Use non-greedy when appropriate     │  Always use greedy quantifiers       │
│  Comment complex patterns (VERBOSE)   │  Write cryptic patterns             │
│  Validate and sanitize input         │  Trust user input blindly            │
└─────────────────────────────────────────────────────────────────────────────┘
```

```python
import re

# ❌ BAD: Compiling in loop
def bad_search(texts, pattern):
    results = []
    for text in texts:
        # Compiles pattern every iteration!
        if re.search(pattern, text):
            results.append(text)
    return results

# ✅ GOOD: Compile once, reuse
def good_search(texts, pattern):
    compiled_pattern = re.compile(pattern)
    results = []
    for text in texts:
        if compiled_pattern.search(text):
            results.append(text)
    return results

# ❌ BAD: Greedy matching for HTML
html = '<div>Hello</div><span>World</span>'
bad_tags = re.findall(r'<.*>', html)
print(f"Bad: {bad_tags}")  # ['<div>Hello</div><span>World</span>']

# ✅ GOOD: Non-greedy matching
good_tags = re.findall(r'<.*?>', html)
print(f"Good: {good_tags}")  # ['<div>', '</div>', '<span>', '</span>']

# ❌ BAD: No input validation
def unsafe_email_extract(text):
    # What if text is None or not a string?
    return re.findall(r'\S+@\S+', text)

# ✅ GOOD: Input validation
def safe_email_extract(text):
    if not isinstance(text, str):
        return []
    try:
        return re.findall(r'\S+@\S+', text)
    except re.error as e:
        print(f"Regex error: {e}")
        return []

# Performance comparison
import time

texts = ["hello world", "test string", "another test"] * 1000
pattern = r"\w+orld"

# Time the bad approach
start = time.time()
bad_search(texts, pattern)
bad_time = time.time() - start

# Time the good approach  
start = time.time()
good_search(texts, pattern)
good_time = time.time() - start

print(f"\nPerformance comparison:")
print(f"Bad approach: {bad_time:.4f} seconds")
print(f"Good approach: {good_time:.4f} seconds")
print(f"Improvement: {bad_time/good_time:.1f}x faster")
```

### 🐛 Common Mistakes and Solutions

```python
import re

# Mistake 1: Forgetting to escape special characters
print("❌ Common Mistake: Special characters")
text = "Price: $19.99"

# Wrong - . matches any character
wrong = re.findall(r"\$\d+.\d+", text)
print(f"Wrong (. matches any): {wrong}")  # Matches $19X99 too!

# Right - escape the dot
right = re.findall(r"\$\d+\.\d+", text)
print(f"Right (escaped .): {right}")

print("\n" + "="*50)

# Mistake 2: Using capture groups when you don't need them
print("❌ Common Mistake: Unnecessary capture groups")
text2 = "Visit http://example.com and https://test.org"

# Inefficient - captures protocol unnecessarily
inefficient = re.findall(r"(http|https)://(\w+\.\w+)", text2)
print(f"Inefficient: {inefficient}")  # [('http', 'example.com'), ...]

# Better - non-capturing group for protocol
efficient = re.findall(r"(?:http|https)://(\w+\.\w+)", text2)
print(f"Efficient: {efficient}")     # ['example.com', 'test.org']

print("\n" + "="*50)

# Mistake 3: Not handling case sensitivity
print("❌ Common Mistake: Case sensitivity")
text3 = "HTML and html and Html"

# Misses variations
case_sensitive = re.findall(r"html", text3)
print(f"Case sensitive: {case_sensitive}")  # ['html']

# Catches all variations
case_insensitive = re.findall(r"html", text3, re.IGNORECASE)
print(f"Case insensitive: {case_insensitive}")  # ['HTML', 'html', 'Html']

print("\n" + "="*50)

# Mistake 4: Catastrophic backtracking
print("❌ Common Mistake: Catastrophic backtracking")

# This pattern can be VERY slow on certain inputs
dangerous_pattern = r"(a+)+"
# Better alternative
safe_pattern = r"a+"

test_string = "a" * 20 + "b"  # 20 a's followed by b

# The dangerous pattern would take exponential time
# The safe pattern is linear time
safe_result = re.search(safe_pattern, test_string)
print(f"Safe pattern result: {safe_result}")

print("\n" + "="*50)

# Mistake 5: Not validating regex patterns
print("❌ Common Mistake: Invalid patterns")

def safe_regex_search(pattern, text):
    """Safely execute regex with error handling"""
    try:
        return re.search(pattern, text)
    except re.error as e:
        print(f"Invalid regex pattern '{pattern}': {e}")
        return None

# These patterns have errors
invalid_patterns = [
    r"[a-z",      # Missing closing bracket
    r"(?P<name>", # Unclosed group
    r"*abc",      # Nothing to repeat
]

for pattern in invalid_patterns:
    result = safe_regex_search(pattern, "test")
    print(f"Pattern '{pattern}': {result}")
```

### 🚀 Performance Tips

```python
import re
import time

def benchmark_regex(pattern, text, iterations=100000):
    """Benchmark regex performance"""
    
    # Test compiled vs non-compiled
    start = time.time()
    for _ in range(iterations):
        re.search(pattern, text)
    non_compiled_time = time.time() - start
    
    compiled_pattern = re.compile(pattern)
    start = time.time()
    for _ in range(iterations):
        compiled_pattern.search(text)
    compiled_time = time.time() - start
    
    print(f"Non-compiled: {non_compiled_time:.4f}s")
    print(f"Compiled: {compiled_time:.4f}s")
    print(f"Speedup: {non_compiled_time/compiled_time:.1f}x\n")

# Performance tips demo
text = "The quick brown fox jumps over the lazy dog" * 100

print("📈 Performance Benchmarks:")
print("=" * 40)

# 1. Simple pattern
print("1. Simple word search:")
benchmark_regex(r"fox", text)

# 2. Complex pattern
print("2. Complex email-like pattern:")
benchmark_regex(r"[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}", text)

# 3. Anchored pattern (faster when match is at start)
print("3. Anchored pattern:")
benchmark_regex(r"^The", text)

# Tips summary
print("🎯 Performance Tips:")
print("1. Compile patterns you use repeatedly")
print("2. Use specific character classes instead of .")
print("3. Anchor patterns when possible (^ and $)")
print("4. Use non-capturing groups (?:) when you don't need captures")
print("5. Be careful with nested quantifiers (* inside +)")
print("6. Use possessive quantifiers (*+) to prevent backtracking")
print("7. Test patterns with realistic data sizes")
```

---

## 🎓 Advanced Exercises and Challenges

### 🏋️ Practice Problems

```python
import re

# Exercise 1: Extract structured data
def parse_invoice_data(text):
    """
    Extract invoice information:
    - Invoice number (INV-XXXX)
    - Date (YYYY-MM-DD or MM/DD/YYYY)
    - Total amount ($XX.XX)
    """
    
    patterns = {
        'invoice_number': r'INV-\d{4}',
        'date_iso': r'\d{4}-\d{2}-\d{2}',
        'date_us': r'\d{2}/\d{2}/\d{4}',
        'amount': r'\$\d+\.\d{2}'
    }
    
    results = {}
    for key, pattern in patterns.items():
        match = re.search(pattern, text)
        results[key] = match.group() if match else None
    
    return results

# Exercise 2: Clean and validate data
def clean_phone_list(phone_list):
    """
    Clean a list of phone numbers to standard format (XXX) XXX-XXXX
    Remove invalid entries
    """
    cleaned = []
    pattern = r'\d'
    
    for phone in phone_list:
        digits = ''.join(re.findall(pattern, phone))
        
        if len(digits) == 10:
            formatted = f"({digits[:3]}) {digits[3:6]}-{digits[6:]}"
            cleaned.append(formatted)
        elif len(digits) == 11 and digits[0] == '1':
            digits = digits[1:]  # Remove country code
            formatted = f"({digits[:3]}) {digits[3:6]}-{digits[6:]}"
            cleaned.append(formatted)
    
    return cleaned

# Exercise 3: Password strength checker
def check_password_strength(password):
    """
    Check password strength:
    - At least 8 characters
    - Contains uppercase letter
    - Contains lowercase letter
    - Contains digit
    - Contains special character
    """
    
    checks = {
        'length': len(password) >= 8,
        'uppercase': bool(re.search(r'[A-Z]', password)),
        'lowercase': bool(re.search(r'[a-z]', password)),
        'digit': bool(re.search(r'\d', password)),
        'special': bool(re.search(r'[!@#$%^&*(),.?":{}|<>]', password))
    }
    
    score = sum(checks.values())
    strength = ['Very Weak', 'Weak', 'Fair', 'Good', 'Strong'][min(score, 4)]
    
    return {
        'score': f"{score}/5",
        'strength': strength,
        'checks': checks,
        'is_valid': score >= 4
    }

# Test the exercises
print("🎯 Exercise Solutions:")
print("=" * 50)

# Test 1: Invoice parsing
invoice_text = """
Invoice Number: INV-1234
Date: 2024-03-15
Amount Due: $156.78
Due Date: 03/30/2024
"""

invoice_data = parse_invoice_data(invoice_text)
print("1. Invoice Data:", invoice_data)

# Test 2: Phone cleaning
messy_phones = [
    "123-456-7890",
    "(987) 654-3210",
    "555.123.4567",
    "1-800-555-0199",
    "123-45-6789",  # Invalid
    "abcd-efg-hijk"  # Invalid
]

clean_phones = clean_phone_list(messy_phones)
print("\n2. Cleaned Phones:", clean_phones)

# Test 3: Password strength
test_passwords = [
    "password",          # Weak
    "Password1",         # Good  
    "P@ssw0rd!",        # Strong
    "12345678",          # Weak
    "MyStr0ng!P@ss"     # Strong
]

print("\n3. Password Strength:")
for pwd in test_passwords:
    result = check_password_strength(pwd)
    print(f"  {pwd:15} → {result['strength']:10} ({result['score']})")
```

---

## 🎉 Conclusion

Congratulations! You've mastered Python Regular Expressions! 🎊

### 🚀 What You've Learned:

```ascii
┌─────────────────────────────────────────────────────────────────────────────┐
│                           🎓 Your RegEx Journey                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ✅ Basic patterns and metacharacters                                      │
│  ✅ Quantifiers and repetition control                                     │
│  ✅ Character classes and custom sets                                      │
│  ✅ Groups, capturing, and backreferences                                  │
│  ✅ Flags and modifiers                                                    │
│  ✅ Advanced techniques (lookahead/behind)                                 │
│  ✅ Real-world applications                                                │
│  ✅ Performance optimization                                               │
│  ✅ Best practices and common pitfalls                                     │
│                                                                            │
│  🏆 You're now a RegEx Master! 🏆                                          │
└────────────────────────────────────────────────────────────────────────────┘
```

### 📚 Continue Your Learning:

- **Practice**: Use regex in your daily coding tasks
- **Experiment**: Try different patterns and see what works
- **Optimize**: Profile your regex patterns for performance
- **Share**: Help others learn regex patterns
- **Build**: Create your own regex-powered tools

### 🔗 Quick Reference:

| Pattern | Meaning | Example |
|---------|---------|---------|
| `.` | Any character | `a.c` matches `abc`, `axc` |
| `\d` | Digit | `\d+` matches `123` |
| `\w` | Word character | `\w+` matches `hello` |
| `\s` | Whitespace | `\s+` matches spaces/tabs |
| `*` | 0 or more | `ab*` matches `a`, `ab`, `abb` |
| `+` | 1 or more | `ab+` matches `ab`, `abb` |
| `?` | 0 or 1 | `ab?` matches `a`, `ab` |
| `^` | Start of string | `^hello` |
| `$` | End of string | `world$` |
| `[]` | Character set | `[aeiou]` matches vowels |
| `()` | Group | `(ab)+` matches `ab`, `abab` |

**Happy Regex-ing!** 🐍✨

---

*Created with ❤️ for Python developers everywhere. Keep coding, keep learning!*