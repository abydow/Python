# 🐍 Python Built-in Modules: Complete Interactive Guide

[![Python modules](https://img.shields.io/badge/Python-BuiltIn%20Modules-blue?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
![Topic](https://img.shields.io/badge/Topic-python%20Modules-green?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-Beginner%20to%20Advanced-orange?style=for-the-badge)


---

## 📖 Table of Contents

1. [🚀 Introduction](#-introduction)
2. [📂 Module Categories](#-module-categories)
3. [🔧 Essential System Modules](#-essential-system-modules)
4. [🗃️ Data Structures & Collections](#️-data-structures--collections)
5. [🕒 Date & Time Modules](#-date--time-modules)
6. [🔢 Mathematical Modules](#-mathematical-modules)
7. [📁 File & Path Operations](#-file--path-operations)
8. [🌐 Network & Internet](#-network--internet)
9. [🛠️ Development & Testing](#️-development--testing)
10. [🎲 Utility Modules](#-utility-modules)
11. [📊 Interactive Examples](#-interactive-examples)
12. [🎯 Best Practices](#-best-practices)
13. [📚 Module Index Quick Reference](#-module-index-quick-reference)

---

## 🚀 Introduction

Python's **built-in modules** are the backbone of Python programming, providing essential functionality without requiring external installations. These modules come pre-packaged with Python and offer solutions for common programming tasks.

```
   ╭───────────────────────────────────────────────────────╮
   │  🌟 Why Built-in Modules Matter?                      │
   │  ┌─────────────────────────────────────────────────┐  │
   │  │ ✅ Always Available                             │  │
   │  │ ✅ Performance Optimized                        │  │
   │  │ ✅ Platform Independent                         │  │
   │  │ ✅ Well Documented                              │  │
   │  │ ✅ Thoroughly Tested                            │  │
   │  └─────────────────────────────────────────────────┘  │
   ╰───────────────────────────────────────────────────────╯
```

### 🎯 What You'll Learn

- **200+ Core Modules** available in Python Standard Library
- **Practical Examples** with real-world applications
- **Best Practices** for module usage
- **Performance Tips** for optimal implementation

---

## 📂 Module Categories

Python's built-in modules can be organized into logical categories:

```
                    ┌─────────────────────────────────────────┐
                    │           PYTHON MODULES                │
                    └──────────────┬──────────────────────────┘
                                   │
          ┌────────────────────────┼────────────────────────┐
          │                        │                        │
    ┌─────▼─────┐         ┌────────▼────────┐      ┌───────▼────────┐
    │  SYSTEM   │         │   DATA & MATH   │      │   NETWORKING   │
    │           │         │                 │      │                │
    │ • os      │         │ • collections   │      │ • socket       │
    │ • sys     │         │ • math          │      │ • http         │
    │ • pathlib │         │ • statistics    │      │ • urllib       │
    │ • shutil  │         │ • decimal       │      │ • json         │
    └───────────┘         └─────────────────┘      └────────────────┘
          │                        │                        │
    ┌─────▼─────┐         ┌────────▼────────┐      ┌───────▼────────┐
    │   TIME    │         │   DEVELOPMENT   │      │    UTILITY     │
    │           │         │                 │      │                │
    │ • time    │         │ • unittest      │      │ • random       │
    │ • datetime│         │ • logging       │      │ • functools    │
    │ • calendar│         │ • pdb           │      │ • itertools    │
    └───────────┘         └─────────────────┘      └────────────────┘
```

---

## 🔧 Essential System Modules

### 📋 `os` Module - Operating System Interface

The `os` module provides a portable way to interact with the operating system.

```
   ╔══════════════════════════════════════╗
   ║            OS MODULE                 ║
   ╠══════════════════════════════════════╣
   ║  Function     │  Purpose             ║
   ║ ──────────────┼────────────────────  ║
   ║  getcwd()     │  Get current dir     ║
   ║  chdir()      │  Change directory    ║
   ║  listdir()    │  List directory      ║
   ║  mkdir()      │  Create directory    ║
   ║  remove()     │  Delete file         ║
   ║  environ      │  Environment vars    ║
   ╚══════════════════════════════════════╝
```

#### 💡 Interactive Example: Directory Operations

```python
import os

# Get current working directory
current_dir = os.getcwd()
print(f"📁 Current Directory: {current_dir}")

# List files in current directory
files = os.listdir('.')
print(f"📄 Files: {files}")

# Create a new directory
os.mkdir('temp_folder')
print("✅ Directory 'temp_folder' created!")

# Environment variables
python_path = os.environ.get('PYTHONPATH', 'Not set')
print(f"🐍 Python Path: {python_path}")
```

### 🎛️ `sys` Module - System-specific Parameters

Access to interpreter variables and functions.

```python
import sys

# Python version information
print(f"🐍 Python Version: {sys.version}")
print(f"📊 Version Info: {sys.version_info}")

# Command line arguments
print(f"📝 Arguments: {sys.argv}")

# Module search paths
print(f"🔍 Python Path: {sys.path}")

# Maximum integer size
print(f"🔢 Max Integer: {sys.maxsize}")
```

### 🛤️ `pathlib` Module - Object-oriented File Paths

Modern approach to file path handling.

```
    Path Object Hierarchy
    ┌─────────────────────┐
    │       PurePath      │
    │   (Path operations) │
    └──────────┬──────────┘
               │
    ┌──────────▼──────────┐
    │        Path         │
    │  (File operations)  │
    └─────────────────────┘
```

#### 🎯 Practical Example: File Path Management

```python
from pathlib import Path

# Create Path objects
home = Path.home()
current = Path.cwd()

print(f"🏠 Home Directory: {home}")
print(f"📁 Current Directory: {current}")

# Path operations
config_file = home / "config" / "settings.json"
print(f"⚙️ Config Path: {config_file}")

# Check if file exists
if config_file.exists():
    print("✅ Config file found!")
else:
    print("❌ Config file not found!")

# Get file properties
for py_file in current.glob("*.py"):
    print(f"🐍 Python File: {py_file.name}")
    print(f"   Size: {py_file.stat().st_size} bytes")
```

---

## 🗃️ Data Structures & Collections

### 📦 `collections` Module - Specialized Data Types

Enhanced data structures beyond built-in types.

```
                    Collections Module
    ┌─────────────────────────────────────────────────────┐
    │                                                     │
    │  ┌─────────────┐  ┌─────────────┐  ┌──────────────┐ │
    │  │ namedtuple  │  │ OrderedDict │  │   Counter    │ │
    │  │             │  │             │  │              │ │
    │  │ Tuple with  │  │ Dict with   │  │ Count freq   │ │
    │  │ named       │  │ order       │  │ of elements  │ │
    │  │ fields      │  │ preserved   │  │              │ │
    │  └─────────────┘  └─────────────┘  └──────────────┘ │
    │                                                     │
    │  ┌─────────────┐  ┌─────────────┐  ┌──────────────┐ │
    │  │   deque     │  │ defaultdict │  │ ChainMap     │ │
    │  │             │  │             │  │              │ │
    │  │ Double-ended│  │ Dict with   │  │ Multiple     │ │
    │  │ queue       │  │ default     │  │ dict views   │ │
    │  │             │  │ factory     │  │              │ │
    │  └─────────────┘  └─────────────┘  └──────────────┘ │
    └─────────────────────────────────────────────────────┘
```

#### 🎲 Interactive Examples

```python
from collections import namedtuple, Counter, deque, defaultdict

# 1. NamedTuple - Structured Data
Person = namedtuple('Person', ['name', 'age', 'email'])
employee = Person('Alice', 30, 'alice@example.com')

print(f"👤 Employee: {employee.name}, Age: {employee.age}")
print(f"📧 Email: {employee.email}")

# 2. Counter - Frequency Counting
text = "hello world"
char_count = Counter(text)
print(f"📊 Character Count: {char_count}")
print(f"🔤 Most Common: {char_count.most_common(3)}")

# 3. Deque - Double-ended Queue
task_queue = deque(['task1', 'task2', 'task3'])
task_queue.appendleft('urgent_task')
task_queue.append('low_priority_task')

print(f"📋 Task Queue: {list(task_queue)}")
current_task = task_queue.popleft()
print(f"⚡ Processing: {current_task}")

# 4. DefaultDict - Auto-initializing Dictionary
word_groups = defaultdict(list)
words = ['apple', 'banana', 'apricot', 'berry', 'cherry']

for word in words:
    word_groups[word[0]].append(word)

print("🔤 Words grouped by first letter:")
for letter, word_list in word_groups.items():
    print(f"   {letter}: {word_list}")
```

---

## 🕒 Date & Time Modules

### 📅 `datetime` Module - Date and Time Handling

Comprehensive date and time operations.

```
               DateTime Objects Hierarchy
    ┌─────────────────────────────────────────────────┐
    │                    datetime                     │
    │                      │                          │
    │  ┌──────────┐  ┌─────▼──────┐  ┌──────────────┐ │
    │  │   date   │  │  datetime  │  │     time     │ │
    │  │          │  │            │  │              │ │
    │  │ Year     │  │ Date +     │  │ Hour         │ │
    │  │ Month    │  │ Time       │  │ Minute       │ │
    │  │ Day      │  │ Combined   │  │ Second       │ │
    │  └──────────┘  └────────────┘  └──────────────┘ │
    │                                                 │
    │  ┌──────────┐  ┌─────────────┐ ┌─────────────┐  │
    │  │timedelta │  │  timezone   │ │    tzinfo   │  │
    │  │          │  │             │ │             │  │
    │  │Duration  │  │ Time zone   │ │ Abstract    │  │
    │  │between   │  │ Info        │ │ timezone    │  │
    │  │dates     │  │             │ │ base class  │  │
    │  └──────────┘  └─────────────┘ └─────────────┘  │
    └─────────────────────────────────────────────────┘
```

#### 🕐 Time Operations Examples

```python
from datetime import datetime, date, time, timedelta
import time as time_module

# Current date and time
now = datetime.now()
today = date.today()
current_time = datetime.now().time()

print(f"🕒 Current DateTime: {now}")
print(f"📅 Today's Date: {today}")
print(f"⏰ Current Time: {current_time}")

# Date arithmetic
tomorrow = today + timedelta(days=1)
next_week = today + timedelta(weeks=1)
past_month = today - timedelta(days=30)

print(f"🌅 Tomorrow: {tomorrow}")
print(f"📆 Next Week: {next_week}")
print(f"📜 Past Month: {past_month}")

# Date formatting
formatted_date = now.strftime("%Y-%m-%d %H:%M:%S")
readable_date = now.strftime("%B %d, %Y at %I:%M %p")

print(f"💾 Formatted: {formatted_date}")
print(f"📖 Readable: {readable_date}")

# Parse date from string
date_string = "2024-12-25"
parsed_date = datetime.strptime(date_string, "%Y-%m-%d")
print(f"🎄 Parsed Date: {parsed_date}")
```

### ⏱️ `time` Module - Time-related Functions

Low-level time operations and measurements.

```python
import time

# Current timestamp
timestamp = time.time()
print(f"🕐 Unix Timestamp: {timestamp}")

# Human-readable time
readable_time = time.ctime()
print(f"📖 Readable Time: {readable_time}")

# Time structure
time_struct = time.localtime()
print(f"📊 Time Structure: {time_struct}")

# Formatted time
formatted = time.strftime("%Y-%m-%d %H:%M:%S")
print(f"✨ Formatted: {formatted}")

# Sleep function demo
print("😴 Sleeping for 2 seconds...")
time.sleep(2)
print("⏰ Wake up!")
```

---

## 🔢 Mathematical Modules

### 🧮 `math` Module - Mathematical Functions

Essential mathematical operations and constants.

```
                    Math Module Functions
    ┌────────────────────────────────────────────┐
    │                                            │
    │  ┌─────────────────┐  ┌─────────────────┐  │
    │  │  TRIGONOMETRIC  │  │   LOGARITHMIC   │  │
    │  │                 │  │                 │  │
    │  │  • sin(x)       │  │  • log(x)       │  │
    │  │  • cos(x)       │  │  • log10(x)     │  │
    │  │  • tan(x)       │  │  • log2(x)      │  │
    │  │  • asin(x)      │  │  • exp(x)       │  │
    │  │  • acos(x)      │  │                 │  │
    │  │  • atan(x)      │  │                 │  │
    │  └─────────────────┘  └─────────────────┘  │
    │                                            │
    │  ┌─────────────────┐  ┌─────────────────┐  │
    │  │     POWER       │  │    ROUNDING     │  │
    │  │                 │  │                 │  │
    │  │  • pow(x, y)    │  │  • ceil(x)      │  │
    │  │  • sqrt(x)      │  │  • floor(x)     │  │
    │  │  • cbrt(x)      │  │  • trunc(x)     │  │
    │  │                 │  │  • round(x)     │  │
    │  └─────────────────┘  └─────────────────┘  │
    │                                            │
    │  ┌─────────────────┐  ┌─────────────────┐  │
    │  │    CONSTANTS    │  │    SPECIAL      │  │
    │  │                 │  │                 │  │
    │  │  • pi           │  │  • factorial(x) │  │
    │  │  • e            │  │  • gcd(a, b)    │  │
    │  │  • tau          │  │  • lcm(a, b)    │  │
    │  │  • inf          │  │  • isqrt(x)     │  │
    │  │  • nan          │  │                 │  │
    │  └─────────────────┘  └─────────────────┘  │
    └────────────────────────────────────────────┘
```

#### 🎯 Mathematical Examples

```python
import math

# Mathematical constants
print(f"🥧 Pi: {math.pi}")
print(f"📈 e: {math.e}")
print(f"🌀 Tau: {math.tau}")

# Basic operations
print(f"√16 = {math.sqrt(16)}")
print(f"2³ = {math.pow(2, 3)}")
print(f"5! = {math.factorial(5)}")

# Trigonometric functions
angle = math.pi / 4  # 45 degrees in radians
print(f"sin(45°) = {math.sin(angle):.4f}")
print(f"cos(45°) = {math.cos(angle):.4f}")
print(f"tan(45°) = {math.tan(angle):.4f}")

# Logarithmic functions
print(f"log₁₀(100) = {math.log10(100)}")
print(f"ln(e) = {math.log(math.e)}")
print(f"log₂(8) = {math.log2(8)}")

# Rounding functions
number = 3.14159
print(f"ceil({number}) = {math.ceil(number)}")
print(f"floor({number}) = {math.floor(number)}")
print(f"trunc({number}) = {math.trunc(number)}")
```

### 📊 `statistics` Module - Statistical Functions

Statistical calculations made easy.

```python
import statistics

# Sample data
data = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
scores = [85, 90, 78, 92, 88, 95, 87, 91, 89, 93]

print("📊 Statistical Analysis")
print("=" * 30)

# Measures of central tendency
print(f"📈 Mean: {statistics.mean(data)}")
print(f"📊 Median: {statistics.median(data)}")
print(f"🎯 Mode: {statistics.mode([1,1,2,2,2,3,3])}")

# Measures of spread
print(f"📏 Range: {max(data) - min(data)}")
print(f"📐 Standard Deviation: {statistics.stdev(data):.2f}")
print(f"📦 Variance: {statistics.variance(data):.2f}")

# Quantiles
print(f"🔢 Quartiles: {statistics.quantiles(data, n=4)}")

# Harmonic and geometric means
print(f"🎼 Harmonic Mean: {statistics.harmonic_mean(data):.2f}")
print(f"📐 Geometric Mean: {statistics.geometric_mean(data):.2f}")
```

---

## 📁 File & Path Operations

### 📄 File Handling Modules

```
                    File Operations Ecosystem
    ┌─────────────────────────────────────────────────────────┐
    │                                                         │
    │  ┌─────────────┐  ┌─────────────┐  ┌─────────────────┐  │
    │  │   pathlib   │  │    glob     │  │     shutil      │  │
    │  │             │  │             │  │                 │  │
    │  │ OOP path    │  │ Pattern     │  │ High-level      │  │
    │  │ handling    │  │ matching    │  │ file ops        │  │
    │  └─────────────┘  └─────────────┘  └─────────────────┘  │
    │                                                         │
    │  ┌─────────────┐  ┌─────────────┐  ┌─────────────────┐  │
    │  │ fileinput   │  │  tempfile   │  │     fnmatch     │  │
    │  │             │  │             │  │                 │  │
    │  │ Line-by-    │  │ Temporary   │  │ Shell-style     │  │
    │  │ line input  │  │ files       │  │ wildcards       │  │
    │  └─────────────┘  └─────────────┘  └─────────────────┘  │
    └─────────────────────────────────────────────────────────┘
```

#### 🔍 `glob` Module - Pattern Matching

```python
import glob
from pathlib import Path

print("🔍 Finding files with glob patterns:")

# Find all Python files
python_files = glob.glob("*.py")
print(f"🐍 Python files: {python_files}")

# Find files recursively
all_python = glob.glob("**/*.py", recursive=True)
print(f"🔄 All Python files (recursive): {len(all_python)} found")

# Pattern matching examples
print("\n📋 Pattern Examples:")
patterns = {
    "*.txt": "All text files",
    "test_*.py": "Test Python files",
    "[0-9]*.log": "Log files starting with number",
    "**/*config*": "Any file with 'config' in name"
}

for pattern, description in patterns.items():
    matches = glob.glob(pattern, recursive=True)
    print(f"   {pattern:<15} → {description} ({len(matches)} found)")
```

#### 🗃️ `shutil` Module - File Operations

```python
import shutil
import os

print("📁 High-level File Operations with shutil:")

# Copy operations
try:
    # Copy file
    # shutil.copy2('source.txt', 'destination.txt')
    print("✅ File copied successfully")
    
    # Copy directory tree
    # shutil.copytree('source_dir', 'backup_dir')
    print("✅ Directory tree copied")
    
except Exception as e:
    print(f"❌ Error: {e}")

# Move operations
# shutil.move('old_location', 'new_location')

# Archive operations
print("\n📦 Archive Operations:")
archive_formats = shutil.get_archive_formats()
for format_name, description in archive_formats:
    print(f"   📦 {format_name}: {description}")

# Disk usage
total, used, free = shutil.disk_usage('/')
print(f"\n💾 Disk Usage:")
print(f"   Total: {total // (2**30)} GB")
print(f"   Used:  {used // (2**30)} GB")
print(f"   Free:  {free // (2**30)} GB")
```

---

## 🌐 Network & Internet

### 🌍 `urllib` Module - URL Handling

```
                     urllib Package Structure
    ┌─────────────────────────────────────────────────────────┐
    │                    urllib                               │
    │                      │                                  │
    │  ┌───────────────────┼───────────────────────────────┐  │
    │  │                   │                               │  │
    │  ▼                   ▼                               ▼  │
    │ ┌─────────────┐ ┌─────────────┐ ┌─────────────────────┐ │
    │ │   request   │ │    parse    │ │       error         │ │
    │ │             │ │             │ │                     │ │
    │ │ • urlopen   │ │ • urlparse  │ │ • URLError          │ │
    │ │ • Request   │ │ • urljoin   │ │ • HTTPError         │ │
    │ │ • HTTPError │ │ • quote     │ │                     │ │
    │ └─────────────┘ └─────────────┘ └─────────────────────┘ │
    │                                                         │
    │ ┌─────────────┐ ┌─────────────┐                         │
    │ │ robotparser │ │   response  │                         │
    │ │             │ │             │                         │
    │ │ • RobotFile │ │ • HTTPResp  │                         │
    │ │ Parser      │ │ • FileResp  │                         │
    │ └─────────────┘ └─────────────┘                         │
    └─────────────────────────────────────────────────────────┘
```

#### 🌐 URL Operations Example

```python
from urllib.parse import urlparse, urljoin, quote, unquote
from urllib.request import urlopen
import json

# URL parsing
url = "https://api.github.com/users/python/repos?type=public&sort=updated"
parsed = urlparse(url)

print("🔗 URL Parsing:")
print(f"   Scheme: {parsed.scheme}")
print(f"   Domain: {parsed.netloc}")
print(f"   Path: {parsed.path}")
print(f"   Query: {parsed.query}")

# URL joining
base = "https://api.example.com/"
endpoint = "users/123"
full_url = urljoin(base, endpoint)
print(f"🔗 Joined URL: {full_url}")

# URL encoding
search_query = "python programming"
encoded = quote(search_query)
print(f"🔐 Encoded: {encoded}")
print(f"🔓 Decoded: {unquote(encoded)}")

# Simple HTTP request example (commented to avoid actual web calls)
# try:
#     with urlopen('https://httpbin.org/json') as response:
#         data = json.loads(response.read())
#         print(f"📊 Response data: {data}")
# except Exception as e:
#     print(f"❌ Error: {e}")
```

### 📡 `json` Module - JSON Data Handling

```python
import json

# Sample data
data = {
    "name": "Alice Developer",
    "age": 30,
    "skills": ["Python", "JavaScript", "Docker"],
    "active": True,
    "projects": {
        "current": "Web API",
        "count": 15
    }
}

print("📊 JSON Operations:")

# Convert to JSON string
json_string = json.dumps(data, indent=2)
print("✨ Pretty JSON:")
print(json_string)

# Parse JSON string
parsed_data = json.loads(json_string)
print(f"\n🔍 Parsed name: {parsed_data['name']}")
print(f"🔍 Skills count: {len(parsed_data['skills'])}")

# Working with files (example)
# with open('data.json', 'w') as f:
#     json.dump(data, f, indent=2)
# 
# with open('data.json', 'r') as f:
#     loaded_data = json.load(f)

print("\n⚙️ JSON Formatting Options:")
print("Compact:", json.dumps(data, separators=(',', ':')))
print("Sorted keys:", json.dumps(data, sort_keys=True))
```

---

## 🛠️ Development & Testing

### 🧪 `unittest` Module - Unit Testing

```
                    Testing Framework Structure
    ┌─────────────────────────────────────────────────────────┐
    │                   unittest                              │
    │                                                         │
    │  ┌─────────────┐  ┌─────────────┐  ┌─────────────────┐  │
    │  │  TestCase   │  │ TestSuite   │  │   TestRunner    │  │
    │  │             │  │             │  │                 │  │
    │  │ • setUp()   │  │ Collection  │  │ Executes        │  │
    │  │ • tearDown()│  │ of test     │  │ tests and       │  │
    │  │ • assert*() │  │ cases       │  │ reports         │  │
    │  └─────────────┘  └─────────────┘  └─────────────────┘  │
    │                                                         │
    │  ┌─────────────┐  ┌─────────────┐  ┌─────────────────┐  │
    │  │    Mock     │  │   Fixture   │  │    Discovery    │  │
    │  │             │  │             │  │                 │  │
    │  │ Test        │  │ Test data   │  │ Automatic       │  │
    │  │ doubles     │  │ setup       │  │ test finding    │  │
    │  └─────────────┘  └─────────────┘  └─────────────────┘  │
    └─────────────────────────────────────────────────────────┘
```

#### 🔬 Unit Testing Example

```python
import unittest

class Calculator:
    def add(self, a, b):
        return a + b
    
    def divide(self, a, b):
        if b == 0:
            raise ValueError("Cannot divide by zero")
        return a / b

class TestCalculator(unittest.TestCase):
    def setUp(self):
        """Set up test fixtures before each test method."""
        self.calc = Calculator()
    
    def test_add_positive_numbers(self):
        """Test adding positive numbers."""
        result = self.calc.add(2, 3)
        self.assertEqual(result, 5)
    
    def test_add_negative_numbers(self):
        """Test adding negative numbers."""
        result = self.calc.add(-2, -3)
        self.assertEqual(result, -5)
    
    def test_divide_normal(self):
        """Test normal division."""
        result = self.calc.divide(10, 2)
        self.assertEqual(result, 5.0)
    
    def test_divide_by_zero(self):
        """Test division by zero raises exception."""
        with self.assertRaises(ValueError):
            self.calc.divide(10, 0)
    
    def tearDown(self):
        """Clean up after each test method."""
        pass

# Run tests
if __name__ == '__main__':
    print("🧪 Running Unit Tests:")
    unittest.main(verbosity=2, exit=False)
```

### 📝 `logging` Module - Application Logging

```python
import logging
import sys

# Configure logging
logging.basicConfig(
    level=logging.DEBUG,
    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s',
    handlers=[
        logging.StreamHandler(sys.stdout),
        # logging.FileHandler('app.log')  # Uncomment to log to file
    ]
)

logger = logging.getLogger('MyApp')

print("📝 Logging Examples:")

# Different log levels
logger.debug("🔍 Debug: Detailed diagnostic info")
logger.info("ℹ️ Info: General application flow")
logger.warning("⚠️ Warning: Something unexpected happened")
logger.error("❌ Error: Serious problem occurred")
logger.critical("💥 Critical: Application may stop")

# Logging with variables
user_id = 12345
action = "login"
logger.info(f"👤 User {user_id} performed action: {action}")

# Exception logging
try:
    result = 10 / 0
except ZeroDivisionError as e:
    logger.exception("🚨 Exception occurred during calculation")
```

---

## 🎲 Utility Modules

### 🎯 `random` Module - Random Number Generation

```
                    Random Module Functions
    ┌────────────────────────────────────────────┐
    │                                            │
    │  ┌─────────────────┐  ┌─────────────────┐  │
    │  │     BASIC       │  │    SEQUENCES    │  │
    │  │                 │  │                 │  │
    │  │  • random()     │  │  • choice()     │  │
    │  │  • uniform()    │  │  • choices()    │  │
    │  │  • randint()    │  │  • shuffle()    │  │
    │  │  • randrange()  │  │  • sample()     │  │
    │  └─────────────────┘  └─────────────────┘  │
    │                                            │
    │  ┌─────────────────┐  ┌─────────────────┐  │
    │  │ DISTRIBUTIONS   │  │      SEED       │  │
    │  │                 │  │                 │  │
    │  │  • gauss()      │  │  • seed()       │  │
    │  │  • normalvariate│  │  • getstate()   │  │
    │  │  • expovariate()│  │  • setstate()   │  │
    │  │  • betavariate()│  │                 │  │
    │  └─────────────────┘  └─────────────────┘  │
    └────────────────────────────────────────────┘
```

#### 🎲 Random Operations Examples

```python
import random

print("🎲 Random Number Generation:")

# Basic random numbers
print(f"Float [0,1): {random.random():.4f}")
print(f"Integer [1,10]: {random.randint(1, 10)}")
print(f"Range [0,100,5): {random.randrange(0, 100, 5)}")
print(f"Uniform [10,20]: {random.uniform(10, 20):.2f}")

# Working with sequences
colors = ['red', 'blue', 'green', 'yellow', 'purple']
print(f"\n🎨 Working with sequences:")
print(f"Random choice: {random.choice(colors)}")
print(f"Multiple choices: {random.choices(colors, k=3)}")
print(f"Sample (no replacement): {random.sample(colors, 3)}")

# Shuffling
deck = list(range(1, 14)) * 4  # Card deck simulation
random.shuffle(deck)
print(f"🃏 Shuffled deck (first 10): {deck[:10]}")

# Statistical distributions
print(f"\n📊 Statistical Distributions:")
print(f"Normal (μ=0, σ=1): {random.gauss(0, 1):.3f}")
print(f"Exponential (λ=1): {random.expovariate(1):.3f}")

# Reproducible randomness
random.seed(42)
print(f"\n🌱 Seeded random: {[random.randint(1,10) for _ in range(5)]}")
random.seed(42)  # Same seed
print(f"Same seed again: {[random.randint(1,10) for _ in range(5)]}")
```

### 🔧 `functools` Module - Higher-order Functions

```python
from functools import lru_cache, reduce, partial, wraps
import time

print("🔧 Functional Programming Tools:")

# 1. LRU Cache for memoization
@lru_cache(maxsize=128)
def fibonacci(n):
    """Fibonacci with memoization."""
    if n < 2:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

start = time.time()
result = fibonacci(30)
end = time.time()
print(f"📈 Fibonacci(30) = {result} (cached, {end-start:.4f}s)")
print(f"💾 Cache info: {fibonacci.cache_info()}")

# 2. Reduce for aggregation
numbers = [1, 2, 3, 4, 5]
sum_result = reduce(lambda x, y: x + y, numbers)
product_result = reduce(lambda x, y: x * y, numbers)
print(f"➕ Sum using reduce: {sum_result}")
print(f"✖️ Product using reduce: {product_result}")

# 3. Partial application
def multiply(x, y, z):
    return x * y * z

double = partial(multiply, 2)  # Fix first argument
print(f"🔢 double(3, 4) = {double(3, 4)}")

# 4. Decorator with wraps
def timer(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"⏱️ {func.__name__} took {end-start:.4f}s")
        return result
    return wrapper

@timer
def slow_function():
    time.sleep(0.1)
    return "Done!"

slow_function()
```

### 🔄 `itertools` Module - Iterator Building Blocks

```python
import itertools

print("🔄 Iterator Tools:")

# Infinite iterators
print("♾️ Infinite Iterators:")
count_iter = itertools.count(10, 2)  # Start at 10, step by 2
print(f"Count: {list(itertools.islice(count_iter, 5))}")

cycle_iter = itertools.cycle(['A', 'B', 'C'])
print(f"Cycle: {list(itertools.islice(cycle_iter, 8))}")

repeat_iter = itertools.repeat('X', 4)
print(f"Repeat: {list(repeat_iter)}")

# Finite iterators
print("\n🔢 Finite Iterators:")
numbers = [1, 2, 3, 4, 5]

# Accumulate (cumulative operations)
cumulative_sum = list(itertools.accumulate(numbers))
cumulative_product = list(itertools.accumulate(numbers, lambda x, y: x * y))
print(f"Cumulative sum: {cumulative_sum}")
print(f"Cumulative product: {cumulative_product}")

# Chain (flatten sequences)
list1 = [1, 2, 3]
list2 = ['a', 'b', 'c']
chained = list(itertools.chain(list1, list2))
print(f"Chained: {chained}")

# Combinations and permutations
print("\n🎯 Combinations & Permutations:")
items = ['A', 'B', 'C', 'D']
combinations = list(itertools.combinations(items, 2))
permutations = list(itertools.permutations(items, 2))
print(f"Combinations (2): {combinations}")
print(f"Permutations (2): {permutations[:6]}...")  # First 6 only

# Grouping
print("\n📊 Grouping:")
data = [('A', 1), ('A', 2), ('B', 3), ('B', 4), ('C', 5)]
grouped = itertools.groupby(data, key=lambda x: x[0])
for key, group in grouped:
    print(f"Group {key}: {list(group)}")
```

---

## 📊 Interactive Examples

### 🎮 Complete Example: File Analysis Tool

Let's build a comprehensive file analysis tool using multiple built-in modules:

```python
import os
import pathlib
import collections
import datetime
import json
import hashlib

def analyze_directory(directory_path):
    """Comprehensive directory analysis using multiple built-in modules."""
    
    print(f"🔍 Analyzing Directory: {directory_path}")
    print("=" * 50)
    
    path = pathlib.Path(directory_path)
    if not path.exists():
        print("❌ Directory not found!")
        return
    
    # Initialize collectors
    file_stats = collections.defaultdict(list)
    extension_count = collections.Counter()
    size_distribution = collections.defaultdict(int)
    
    # Analyze all files
    total_files = 0
    total_size = 0
    
    for file_path in path.rglob("*"):
        if file_path.is_file():
            total_files += 1
            
            # Get file info
            stat_info = file_path.stat()
            file_size = stat_info.st_size
            total_size += file_size
            
            # Modified time
            modified_time = datetime.datetime.fromtimestamp(stat_info.st_mtime)
            
            # Extension analysis
            extension = file_path.suffix.lower() or 'no_extension'
            extension_count[extension] += 1
            
            # Size categorization
            if file_size < 1024:
                size_category = "Small (<1KB)"
            elif file_size < 1024 * 1024:
                size_category = "Medium (<1MB)"
            elif file_size < 1024 * 1024 * 10:
                size_category = "Large (<10MB)"
            else:
                size_category = "Very Large (>10MB)"
            
            size_distribution[size_category] += 1
            
            # Store file info
            file_info = {
                'name': file_path.name,
                'size': file_size,
                'modified': modified_time.isoformat(),
                'extension': extension,
                'relative_path': str(file_path.relative_to(path))
            }
            file_stats[extension].append(file_info)
    
    # Generate report
    report = {
        'analysis_date': datetime.datetime.now().isoformat(),
        'directory': str(path.absolute()),
        'summary': {
            'total_files': total_files,
            'total_size_bytes': total_size,
            'total_size_mb': round(total_size / (1024 * 1024), 2)
        },
        'extension_distribution': dict(extension_count.most_common()),
        'size_distribution': dict(size_distribution),
        'largest_files': []
    }
    
    # Find largest files
    all_files = []
    for ext_files in file_stats.values():
        all_files.extend(ext_files)
    
    largest_files = sorted(all_files, key=lambda x: x['size'], reverse=True)[:10]
    report['largest_files'] = largest_files
    
    # Display results
    print(f"📊 Analysis Results:")
    print(f"   Total Files: {report['summary']['total_files']:,}")
    print(f"   Total Size: {report['summary']['total_size_mb']} MB")
    
    print(f"\n📁 File Extensions:")
    for ext, count in extension_count.most_common(10):
        percentage = (count / total_files) * 100
        print(f"   {ext:<15}: {count:>6} files ({percentage:4.1f}%)")
    
    print(f"\n📏 Size Distribution:")
    for category, count in size_distribution.items():
        percentage = (count / total_files) * 100
        print(f"   {category:<20}: {count:>6} files ({percentage:4.1f}%)")
    
    print(f"\n🏆 Largest Files:")
    for i, file_info in enumerate(largest_files, 1):
        size_mb = file_info['size'] / (1024 * 1024)
        print(f"   {i:2d}. {file_info['name']:<30} ({size_mb:6.2f} MB)")
    
    # Save report to JSON
    report_path = path / "analysis_report.json"
    with open(report_path, 'w') as f:
        json.dump(report, f, indent=2, default=str)
    
    print(f"\n💾 Report saved to: {report_path}")
    
    return report

# Example usage (commented to avoid actual execution)
# analyze_directory(".")
```

---

## 🎯 Best Practices

### ✅ Module Usage Guidelines

```
                    Module Best Practices
    ┌─────────────────────────────────────────────────────────┐
    │                                                         │
    │  ✅ DO                          ❌ DON'T                │
    │  ─────────────────────────────────────────────────────  │
    │                                                         │
    │  • Import specific functions    • Use wildcard imports  │
    │    from module import func        from module import *  │
    │                                                         │
    │  • Use descriptive aliases      • Import entire module  │
    │    import numpy as np             when only need few    │
    │                                   functions             │
    │  • Group imports logically      • Mix standard and      │
    │    - Standard library first       third-party imports   │
    │    - Third-party second          without separation     │
    │    - Local modules last                                 │
    │                                                         │
    │  • Handle exceptions properly   • Ignore error handling │
    │    try: module.function()        module.risky_function()│
    │    except ModuleError: pass                             │
    │                                                         │
    │  • Check module availability    • Assume module exists  │
    │    try: import optional_module   import rare_module     │
    │    except ImportError: pass                             │
    └─────────────────────────────────────────────────────────┘
```

### 🔧 Performance Tips

```python
import time
import functools

# Example: Performance comparison
def performance_demo():
    """Demonstrate performance best practices."""
    
    # 1. Use appropriate data structures
    print("📈 Performance Comparisons:")
    
    # List vs Set for membership testing
    large_list = list(range(10000))
    large_set = set(range(10000))
    
    # Test membership in list
    start = time.time()
    9999 in large_list
    list_time = time.time() - start
    
    # Test membership in set
    start = time.time()
    9999 in large_set
    set_time = time.time() - start
    
    print(f"   List membership: {list_time:.6f}s")
    print(f"   Set membership:  {set_time:.6f}s")
    print(f"   Set is {list_time/set_time:.1f}x faster!")
    
    # 2. Use caching for expensive operations
    @functools.lru_cache(maxsize=None)
    def expensive_operation(n):
        """Simulate expensive computation."""
        time.sleep(0.01)  # Simulate work
        return n ** 2
    
    # First call (slow)
    start = time.time()
    result = expensive_operation(42)
    first_call = time.time() - start
    
    # Second call (fast, cached)
    start = time.time()
    result = expensive_operation(42)
    second_call = time.time() - start
    
    print(f"\n💾 Caching Benefits:")
    print(f"   First call:  {first_call:.4f}s")
    print(f"   Cached call: {second_call:.6f}s")
    print(f"   Speedup: {first_call/second_call:.0f}x faster!")

# performance_demo()  # Uncomment to run
```

---

## 📚 Module Index Quick Reference

### 🏷️ Modules by Category

```
╔═══════════════════════════════════════════════════════════════════════════════════╗
║                           PYTHON BUILT-IN MODULES INDEX                           ║
╠═══════════════════════════════════════════════════════════════════════════════════╣
║                                                                                   ║
║  🔧 SYSTEM & OS                    📊 DATA & COLLECTIONS                          ║
║  ├── os                           ├── collections                                 ║
║  ├── sys                          ├── array                                       ║
║  ├── platform                     ├── heapq                                       ║
║  ├── subprocess                   ├── bisect                                      ║
║  ├── signal                       ├── weakref                                     ║
║  ├── errno                        ├── copy                                        ║
║  ├── ctypes                       ├── pprint                                      ║
║  └── gc                           └── reprlib                                     ║
║                                                                                   ║
║  📁 FILE & PATH                    🔢 MATH & NUMBERS                              ║
║  ├── pathlib                      ├── math                                        ║
║  ├── glob                         ├── cmath                                       ║
║  ├── fnmatch                      ├── decimal                                     ║
║  ├── shutil                       ├── fractions                                   ║
║  ├── tempfile                     ├── random                                      ║
║  ├── fileinput                    ├── statistics                                  ║
║  ├── linecache                    └── numbers                                     ║
║  └── filecmp                                                                      ║
║                                                                                   ║
║  🕒 DATE & TIME                    🔤 TEXT & STRINGS                              ║
║  ├── datetime                     ├── string                                      ║
║  ├── time                         ├── re                                          ║
║  ├── calendar                     ├── difflib                                     ║
║  └── zoneinfo                     ├── textwrap                                    ║
║                                   ├── unicodedata                                 ║
║                                   └── stringprep                                  ║
║                                                                                   ║
║  🌐 NETWORK & WEB                  📦 DATA FORMATS                                ║
║  ├── urllib                       ├── json                                        ║
║  ├── http                         ├── csv                                         ║
║  ├── socket                       ├── pickle                                      ║
║  ├── ssl                          ├── copyreg                                     ║
║  ├── email                        ├── marshal                                     ║
║  ├── smtplib                      ├── xml                                         ║
║  ├── poplib                       ├── html                                        ║
║  ├── ftplib                       ├── configparser                                ║
║  └── webbrowser                   ├── tomllib                                     ║
║                                   ├── base64                                      ║
║                                   ├── binascii                                    ║
║                                   ├── uu                                          ║
║                                   └── bz2, gzip, lzma, zipfile, tarfile           ║
║                                                                                   ║
║  🧪 DEVELOPMENT & DEBUG            🔧 FUNCTIONAL PROGRAMMING                      ║
║  ├── unittest                     ├── functools                                   ║
║  ├── doctest                      ├── itertools                                   ║
║  ├── logging                      ├── operator                                    ║
║  ├── pdb                          └── contextlib                                  ║
║  ├── trace                                                                        ║
║  ├── traceback                    🎲 MISCELLANEOUS                                ║
║  ├── faulthandler                 ├── keyword                                     ║
║  ├── timeit                       ├── token                                       ║
║  ├── profile/cProfile             ├── tokenize                                    ║
║  ├── pstats                       ├── ast                                         ║
║  └── inspect                      ├── dis                                         ║
║                                   ├── code                                        ║
║                                   ├── codeop                                      ║
║                                   ├── types                                       ║
║                                   ├── enum                                        ║
║                                   ├── abc                                         ║
║                                   ├── atexit                                      ║
║                                   ├── warnings                                    ║
║                                   └── getpass                                     ║
╚═══════════════════════════════════════════════════════════════════════════════════╝
```

### 🚀 Quick Command Reference

```bash
# Discover all available modules
python -c "help('modules')"

# Get module information
python -c "import os; help(os)"

# Check module location
python -c "import json; print(json.__file__)"

# List module contents
python -c "import math; print(dir(math))"

# Module documentation
python -m pydoc os
python -m pydoc -b  # Start browser-based documentation
```

---

## 🎉 Conclusion

Python's built-in modules provide a robust foundation for development across various domains. By mastering these modules, you can:

```
    ┌─────────────────────────────────────────────────────┐
    │  🏆 BENEFITS OF MASTERING BUILT-IN MODULES          │
    │                                                     │
    │  ✨ Write more efficient code                       │
    │  🚀 Faster development cycles                       │
    │  🔧 Better problem-solving toolkit                  │
    │  📚 Deeper Python understanding                     │
    │  🎯 Professional code quality                       │
    │  🌟 Reduced external dependencies                   │
    └─────────────────────────────────────────────────────┘
```

### 📖 Next Steps

1. **Practice**: Implement the examples in your own projects
2. **Explore**: Try modules you haven't used before
3. **Combine**: Use multiple modules together for complex tasks
4. **Document**: Keep this reference handy during development
5. **Share**: Teach others what you learn

---

### 🔗 Additional Resources

- **Official Documentation**: [docs.python.org](https://docs.python.org/3/library/)
- **Module of the Week**: [pymotw.com](https://pymotw.com/)
- **Real Python**: Module tutorials and guides
- **Python Enhancement Proposals**: For understanding module design decisions

---

```
             🐍 Happy Python Programming! 🐍
    
    ╭─────────────────────────────────────────────────╮
    │  "The Python Standard Library is where          │
    │   productivity meets elegance."                 │
    │                                                 │
    │            — Python Developer Community         │
    ╰─────────────────────────────────────────────────╯

                     ⭐⭐⭐⭐⭐
                Made with ❤️ and Python
                     ⭐⭐⭐⭐⭐
```