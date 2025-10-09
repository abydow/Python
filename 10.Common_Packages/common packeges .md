# 🐍 Complete Guide to Common Python Packages

<div align="center">

```
    ____        __  __                   
   / __ \__  __/ /_/ /_  ____  ____     
  / /_/ / / / / __/ __ \/ __ \/ __ \    
 / ____/ /_/ / /_/ / / / /_/ / / / /    
/_/    \__, /\__/_/ /_/\____/_/ /_/     
      /____/                           
                                       
  📦 Essential Libraries for Modern Development 📦
```

</div>

---

## 📚 Table of Contents

- [🌐 HTTP Requests - `requests`](#-http-requests---requests)
- [📁 Path Handling - `pathlib`](#-path-handling---pathlib)
- [⚡ Async Programming - `asyncio`](#-async-programming---asyncio)
- [🎯 Data Classes - `dataclasses`](#-data-classes---dataclasses)
- [🔐 Environment Variables - `python-dotenv`](#-environment-variables---python-dotenv)
- [🔢 Numerical Computing - `numpy`](#-numerical-computing---numpy)
- [📊 Data Analysis - `pandas`](#-data-analysis---pandas)
- [🚀 Quick Start Examples](#-quick-start-examples)
- [💡 Best Practices](#-best-practices)
- [🔗 Resources](#-resources)

---

## 🌐 HTTP Requests - `requests`

<div align="center">

```
    ┌─────────────────────────────────────────┐
    │        🌐 HTTP for Humans™️             │
    │                                         │
    │  📡 GET   📤 POST   ✏️ PUT   🗑️ DELETE  │
    │                                         │
    │     Simple • Elegant • Powerful         │
    └─────────────────────────────────────────┘
```

</div>

### 🎯 **What is Requests?**

The **requests** library is an elegant and simple HTTP library for Python, built for human beings. It abstracts the complexities of making HTTP requests behind a beautiful, simple API.

### ✨ **Key Features**

- **Keep-Alive & Connection Pooling** 🔄
- **International Domains and URLs** 🌍  
- **Sessions with Cookie Persistence** 🍪
- **Browser-style SSL Verification** 🔒
- **Automatic Content Decoding** 📝
- **Basic/Digest Authentication** 🔐
- **Elegant Key/Value Cookies** 🍪
- **Automatic Decompression** 📦
- **Unicode Response Bodies** 🌐
- **HTTP(S) Proxy Support** 🔀
- **Multipart File Uploads** 📎
- **Streaming Downloads** ⬇️
- **Connection Timeouts** ⏱️
- **Chunked Requests** 🧩

### 🚀 **Basic Usage**

```python
import requests

# GET request
response = requests.get('https://api.github.com/user', 
                       auth=('user', 'pass'))

print(f"Status Code: {response.status_code}")
print(f"Content Type: {response.headers['content-type']}")
print(f"Encoding: {response.encoding}")

# JSON response
data = response.json()
print(data)
```

### 🎨 **Advanced Examples**

```python
# POST with JSON data
payload = {'key1': 'value1', 'key2': 'value2'}
r = requests.post('https://httpbin.org/post', json=payload)

# File upload
files = {'file': open('report.pdf', 'rb')}
r = requests.post('https://httpbin.org/post', files=files)

# Session with cookies
session = requests.Session()
session.get('https://httpbin.org/cookies/set/sessioncookie/123456789')
r = session.get('https://httpbin.org/cookies')

# Custom headers and timeout
headers = {'User-Agent': 'My App 1.0'}
r = requests.get('https://api.example.com/data', 
                headers=headers, timeout=5)
```

### 🎭 **ASCII Art Demo**

```
    📡 API Request Flow
    
    Client          Server
      |               |
      |--- GET ---->  |
      |               |
      |<-- 200 ----   |  
      |    JSON       |
      |               |
      ✅ Success!     ✨
```

---

## 📁 Path Handling - `pathlib`

<div align="center">

```
    ┌─────────────────────────────────────────┐
    │         📁 Object-Oriented Paths        │
    │                                         │
    │  🗂️ /home/user/project/file.py          │
    │                                         │
    │    Cross-Platform • Intuitive           │
    └─────────────────────────────────────────┘
```

</div>

### 🎯 **What is pathlib?**

**pathlib** offers classes representing filesystem paths with semantics appropriate for different operating systems. It provides an object-oriented approach to handling file system paths.

### ✨ **Key Features**

- **Object-Oriented Design** 🏗️
- **Cross-Platform Compatibility** 🌍
- **Intuitive Path Operations** 🛠️
- **Built-in File Operations** 📂
- **Glob Pattern Matching** 🔍
- **Path Properties** 📋
- **Safe Path Manipulation** 🔒

### 🚀 **Basic Usage**

```python
from pathlib import Path

# Create path objects
current_dir = Path('.')
config_file = Path('/etc/apache2/apache2.conf')
user_home = Path.home()

# Path navigation
project_path = Path('/home/user/projects/myapp')
src_path = project_path / 'src' / 'main.py'

print(f"Project: {project_path}")
print(f"Source: {src_path}")
print(f"Exists: {src_path.exists()}")
```

### 🎨 **Advanced Examples**

```python
from pathlib import Path

# File operations
data_file = Path('data.txt')
data_file.write_text('Hello, World!')
content = data_file.read_text()

# Directory operations
new_dir = Path('my_project')
new_dir.mkdir(parents=True, exist_ok=True)

# File properties
py_file = Path('script.py')
print(f"Name: {py_file.name}")
print(f"Suffix: {py_file.suffix}")
print(f"Stem: {py_file.stem}")
print(f"Parent: {py_file.parent}")

# Glob patterns
python_files = list(Path('.').glob('**/*.py'))
for file in python_files:
    print(file)

# Path manipulation
old_path = Path('old_name.txt')
new_path = old_path.with_name('new_name.txt')
new_path_suffix = old_path.with_suffix('.json')
```

### 🎭 **ASCII Art Demo**

```
    📂 File System Tree
    
    /home/user/
    ├── 📁 projects/
    │   ├── 📁 myapp/
    │   │   ├── 📄 main.py
    │   │   └── 📄 config.json
    │   └── 📁 utils/
    │       └── 📄 helpers.py
    └── 📄 .bashrc
```

---

## ⚡ Async Programming - `asyncio`

<div align="center">

```
    ┌─────────────────────────────────────────┐
    │         ⚡ Asynchronous I/O             │
    │                                         │
    │  🔄 async/await  🎭 Coroutines          │
    │                                         │
    │   Concurrent • Non-blocking • Fast      │
    └─────────────────────────────────────────┘
```

</div>

### 🎯 **What is asyncio?**

**asyncio** is a library to write concurrent code using the async/await syntax. It's perfect for IO-bound and high-level structured network code.

### ✨ **Key Features**

- **async/await Syntax** ⚡
- **Event Loop Management** 🔄
- **Coroutines & Tasks** 🎭
- **Asynchronous I/O** 📡
- **Concurrent Execution** 🏃‍♂️
- **Network Programming** 🌐
- **Subprocess Management** 🖥️
- **Synchronization Primitives** 🔒

### 🚀 **Basic Usage**

```python
import asyncio
import aiohttp
import time

# Basic async function
async def say_hello(name, delay):
    await asyncio.sleep(delay)
    print(f"Hello, {name}!")
    return f"Greeting sent to {name}"

# Running async function
async def main():
    # Sequential execution
    start = time.time()
    await say_hello("Alice", 1)
    await say_hello("Bob", 1)
    print(f"Sequential: {time.time() - start:.2f}s")
    
    # Concurrent execution
    start = time.time()
    results = await asyncio.gather(
        say_hello("Charlie", 1),
        say_hello("Diana", 1),
        say_hello("Eve", 1)
    )
    print(f"Concurrent: {time.time() - start:.2f}s")
    print(results)

# Run the event loop
asyncio.run(main())
```

### 🎨 **Advanced Examples**

```python
import asyncio
import aiohttp
import aiofiles

# Async HTTP requests
async def fetch_data(session, url):
    async with session.get(url) as response:
        return await response.json()

# Async file operations
async def write_data_async(filename, data):
    async with aiofiles.open(filename, 'w') as f:
        await f.write(data)

# Producer-Consumer pattern
async def producer(queue):
    for i in range(5):
        await asyncio.sleep(1)
        await queue.put(f"item-{i}")
        print(f"Produced item-{i}")
    await queue.put(None)  # Signal completion

async def consumer(queue):
    while True:
        item = await queue.get()
        if item is None:
            break
        print(f"Consumed {item}")
        await asyncio.sleep(0.5)

# Task management
async def advanced_example():
    # HTTP requests
    async with aiohttp.ClientSession() as session:
        urls = ['https://api.github.com/users/octocat',
                'https://api.github.com/users/defunkt']
        tasks = [fetch_data(session, url) for url in urls]
        results = await asyncio.gather(*tasks)
        
    # Producer-Consumer
    queue = asyncio.Queue()
    producer_task = asyncio.create_task(producer(queue))
    consumer_task = asyncio.create_task(consumer(queue))
    
    await asyncio.gather(producer_task, consumer_task)

asyncio.run(advanced_example())
```

### 🎭 **ASCII Art Demo**

```
    ⚡ Async Execution Flow
    
    Time →
    Task A: ████░░░░████░░░░████
    Task B: ░░████░░░░████░░░░██
    Task C: ░░░░████░░░░████░░░░
           ├─────────────────────┤
           Concurrent Execution!
```

---

## 🎯 Data Classes - `dataclasses`

<div align="center">

```
    ┌─────────────────────────────────────────┐
    │         🎯 Data Classes                 │
    │                                         │
    │  @dataclass  🏗️  __init__  📝 __repr__  │
    │                                         │
    │     Less Boilerplate • More Features    │
    └─────────────────────────────────────────┘
```

</div>

### 🎯 **What are dataclasses?**

**dataclasses** provide a decorator and functions for automatically adding generated special methods to user-defined classes, reducing boilerplate code.

### ✨ **Key Features**

- **Automatic __init__** 🏗️
- **Automatic __repr__** 📝
- **Automatic __eq__** ⚖️
- **Field Customization** 🎛️
- **Default Values** 💫
- **Frozen Instances** ❄️
- **Post-init Processing** 🔄
- **Inheritance Support** 👨‍👩‍👧‍👦

### 🚀 **Basic Usage**

```python
from dataclasses import dataclass, field
from typing import List

@dataclass
class Product:
    name: str
    price: float
    quantity: int = 0
    tags: List[str] = field(default_factory=list)
    
    def total_value(self) -> float:
        return self.price * self.quantity

# Usage
laptop = Product("MacBook Pro", 2499.99, 5)
print(laptop)
# Output: Product(name='MacBook Pro', price=2499.99, quantity=5, tags=[])

print(f"Total value: ${laptop.total_value()}")
# Output: Total value: $12499.95
```

### 🎨 **Advanced Examples**

```python
from dataclasses import dataclass, field, asdict, astuple
from datetime import datetime
from typing import Optional, List

@dataclass(frozen=True)  # Immutable
class Point:
    x: float
    y: float
    
    def distance_from_origin(self) -> float:
        return (self.x ** 2 + self.y ** 2) ** 0.5

@dataclass
class User:
    username: str
    email: str
    created_at: datetime = field(default_factory=datetime.now)
    is_active: bool = True
    profile_picture: Optional[str] = None
    friends: List[str] = field(default_factory=list)
    
    def __post_init__(self):
        # Custom initialization
        self.email = self.email.lower()
        if not self.email.endswith('@company.com'):
            raise ValueError("Must use company email")

@dataclass
class Order:
    user: User
    products: List[Product] = field(default_factory=list)
    order_date: datetime = field(default_factory=datetime.now)
    
    def add_product(self, product: Product):
        self.products.append(product)
    
    def total_amount(self) -> float:
        return sum(p.total_value() for p in self.products)

# Usage
user = User("john_doe", "john@company.com")
order = Order(user)
order.add_product(Product("Phone", 999.99, 2))

# Convert to dict/tuple
user_dict = asdict(user)
user_tuple = astuple(user)

print(f"Order total: ${order.total_amount()}")
```

### 🎭 **ASCII Art Demo**

```
    🎯 DataClass Magic
    
    @dataclass
    class Hero:        ──┐
        name: str        │ Automatic:
        power: int       │ • __init__
        level: int = 1   │ • __repr__
                       ──┘ • __eq__
    
    hero = Hero("Batman", 95)
    print(hero)  # Hero(name='Batman', power=95, level=1)
```

---

## 🔐 Environment Variables - `python-dotenv`

<div align="center">

```
    ┌─────────────────────────────────────────┐
    │         🔐 Environment Variables        │
    │                                         │
    │   .env  🔑  Config  🛡️  Security        │
    │                                         │
    │    12-Factor App • Configuration        │
    └─────────────────────────────────────────┘
```

</div>

### 🎯 **What is python-dotenv?**

**python-dotenv** reads key-value pairs from a .env file and sets them as environment variables, following 12-factor application principles.

### ✨ **Key Features**

- **12-Factor App Compliance** 📋
- **Development Configuration** 🛠️
- **Environment Isolation** 🏝️
- **Variable Expansion** 🔄
- **Multiple File Support** 📁
- **CLI Interface** 💻
- **IPython Integration** 🐍
- **Secure Configuration** 🔒

### 🚀 **Basic Usage**

Create a `.env` file:
```bash
# .env file
DATABASE_URL=postgresql://user:pass@localhost/db
API_KEY=your-secret-api-key-here
DEBUG=True
MAX_CONNECTIONS=100
```

Python code:
```python
from dotenv import load_dotenv
import os

# Load environment variables
load_dotenv()

# Access variables
db_url = os.getenv('DATABASE_URL')
api_key = os.getenv('API_KEY')
debug = os.getenv('DEBUG', 'False').lower() == 'true'
max_conn = int(os.getenv('MAX_CONNECTIONS', '10'))

print(f"Database: {db_url}")
print(f"Debug mode: {debug}")
print(f"Max connections: {max_conn}")
```

### 🎨 **Advanced Examples**

```python
from dotenv import dotenv_values, find_dotenv, set_key
import os

# Multiple environment files
config = {
    **dotenv_values(".env.shared"),    # shared variables
    **dotenv_values(".env.secret"),    # secret variables  
    **os.environ,                      # override with env variables
}

# Development vs Production
class Config:
    def __init__(self):
        load_dotenv(find_dotenv())
        
        self.DATABASE_URL = os.getenv('DATABASE_URL')
        self.SECRET_KEY = os.getenv('SECRET_KEY')
        self.DEBUG = os.getenv('DEBUG', 'False').lower() == 'true'
        self.REDIS_URL = os.getenv('REDIS_URL', 'redis://localhost:6379')
        
    def validate(self):
        required_vars = ['DATABASE_URL', 'SECRET_KEY']
        missing = [var for var in required_vars if not getattr(self, var)]
        if missing:
            raise ValueError(f"Missing required environment variables: {missing}")

# Load without modifying environment
def load_config_dict(env_file='.env'):
    return dotenv_values(env_file)

# Dynamic configuration
def update_env_var(key, value, env_file='.env'):
    set_key(env_file, key, value)
    load_dotenv(env_file, override=True)

# Usage
config = Config()
config.validate()

# CLI usage examples:
# $ dotenv set API_KEY new-api-key
# $ dotenv list
# $ dotenv run -- python manage.py runserver
```

### 🎭 **ASCII Art Demo**

```
    🔐 Environment Configuration
    
    .env file          →    Environment
    ┌─────────────┐         ┌─────────────┐
    │ DB_HOST=... │   ──→   │ os.environ  │
    │ API_KEY=... │         │   DB_HOST   │
    │ DEBUG=True  │         │   API_KEY   │
    └─────────────┘         │   DEBUG     │
                            └─────────────┘
```

---

## 🔢 Numerical Computing - `numpy`

<div align="center">

```
    ┌─────────────────────────────────────────┐
    │         🔢 Numerical Python             │
    │                                         │
    │  📊 Arrays  🧮 Math  ⚡ Performance     │
    │                                         │
    │    Scientific Computing Foundation      │
    └─────────────────────────────────────────┘
```

</div>

### 🎯 **What is NumPy?**

**NumPy** (Numerical Python) is the fundamental library for scientific computing in Python. It provides a powerful N-dimensional array object and tools for working with arrays.

### ✨ **Key Features**

- **N-dimensional Arrays** 📊
- **Vectorized Operations** ⚡
- **Broadcasting** 📡
- **Linear Algebra** 🧮
- **Random Number Generation** 🎲
- **Fourier Transforms** 🌊
- **Memory Efficiency** 💾
- **C/C++ Integration** 🔗

### 🚀 **Basic Usage**

```python
import numpy as np

# Array creation
arr1d = np.array([1, 2, 3, 4, 5])
arr2d = np.array([[1, 2, 3], [4, 5, 6]])

# Special arrays
zeros = np.zeros((3, 4))
ones = np.ones((2, 3))
identity = np.eye(3)
random = np.random.rand(2, 3)

# Array operations
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print(f"Addition: {a + b}")
print(f"Multiplication: {a * b}")
print(f"Dot product: {np.dot(a, b)}")
print(f"Sum: {np.sum(a)}")
print(f"Mean: {np.mean(a)}")
```

### 🎨 **Advanced Examples**

```python
import numpy as np
import matplotlib.pyplot as plt

# Mathematical operations
x = np.linspace(0, 2*np.pi, 100)
y = np.sin(x)
z = np.cos(x)

# Matrix operations
A = np.random.rand(3, 3)
B = np.random.rand(3, 3)
C = np.dot(A, B)  # Matrix multiplication

# Eigenvalues and eigenvectors
eigenvals, eigenvecs = np.linalg.eig(A)

# Statistics
data = np.random.normal(0, 1, 1000)
mean = np.mean(data)
std = np.std(data)
percentiles = np.percentile(data, [25, 50, 75])

# Array manipulation
original = np.arange(12)
reshaped = original.reshape(3, 4)
transposed = reshaped.T
flattened = reshaped.flatten()

# Boolean indexing
arr = np.array([1, 2, 3, 4, 5, 6])
mask = arr > 3
filtered = arr[mask]  # [4, 5, 6]

# Broadcasting example
matrix = np.array([[1, 2, 3], [4, 5, 6]])
vector = np.array([10, 20, 30])
result = matrix + vector  # Adds vector to each row

print(f"Eigenvalues: {eigenvals}")
print(f"Data stats: mean={mean:.2f}, std={std:.2f}")
print(f"Filtered array: {filtered}")
```

### 🎭 **ASCII Art Demo**

```
    🔢 NumPy Array Operations
    
    [1 2 3]     [4 5 6]
       +           =        [5 7 9]
    
    [[1 2]   ×   [[5 6]   =   [[19 22]
     [3 4]]       [7 8]]       [43 50]]
    
    Vectorized ⚡ Fast ⚡ Efficient
```

---

## 📊 Data Analysis - `pandas`

<div align="center">

```
    ┌─────────────────────────────────────────┐
    │         📊 Data Analysis                │
    │                                         │
    │  📋 DataFrames  📈 Analysis  🔍 Query   │
    │                                         │
    │    Data Manipulation Powerhouse         │
    └─────────────────────────────────────────┘
```

</div>

### 🎯 **What is pandas?**

**pandas** is a powerful data manipulation and analysis library built on top of NumPy. It provides easy-to-use data structures and analysis tools for Python.

### ✨ **Key Features**

- **DataFrame & Series** 📋
- **Data Import/Export** 📁
- **Data Cleaning** 🧹
- **Grouping & Aggregation** 📊
- **Time Series Analysis** ⏰
- **Merging & Joining** 🔗
- **Pivot Tables** 🔄
- **Statistical Analysis** 📈

### 🚀 **Basic Usage**

```python
import pandas as pd
import numpy as np

# Create DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'Diana'],
    'Age': [25, 30, 35, 28],
    'City': ['NYC', 'LA', 'Chicago', 'Boston'],
    'Salary': [70000, 80000, 90000, 75000]
}

df = pd.DataFrame(data)
print(df)

# Basic operations
print(f"Average age: {df['Age'].mean()}")
print(f"Max salary: {df['Salary'].max()}")
print(f"Info:\n{df.info()}")
print(f"Description:\n{df.describe()}")

# Filtering
high_earners = df[df['Salary'] > 75000]
young_people = df[df['Age'] < 30]
```

### 🎨 **Advanced Examples**

```python
import pandas as pd
import numpy as np

# Read data from various sources
# df = pd.read_csv('data.csv')
# df = pd.read_excel('data.xlsx')
# df = pd.read_sql('SELECT * FROM table', connection)

# Create sample data
dates = pd.date_range('2023-01-01', periods=100)
df = pd.DataFrame({
    'date': dates,
    'sales': np.random.randint(100, 1000, 100),
    'region': np.random.choice(['North', 'South', 'East', 'West'], 100),
    'product': np.random.choice(['A', 'B', 'C'], 100)
})

# Data manipulation
df['month'] = df['date'].dt.month
df['quarter'] = df['date'].dt.quarter

# Grouping and aggregation
monthly_sales = df.groupby('month')['sales'].agg({
    'total': 'sum',
    'average': 'mean',
    'count': 'count'
})

regional_analysis = df.groupby(['region', 'product'])['sales'].sum().unstack()

# Pivot tables
pivot = df.pivot_table(
    values='sales',
    index='region',
    columns='product',
    aggfunc='mean'
)

# Time series operations
df.set_index('date', inplace=True)
weekly_sales = df['sales'].resample('W').sum()
rolling_average = df['sales'].rolling(window=7).mean()

# Data cleaning
df_clean = df.dropna()  # Remove missing values
df_filled = df.fillna(df['sales'].mean())  # Fill missing values

# Merging DataFrames
df1 = pd.DataFrame({'A': [1, 2], 'B': [3, 4]})
df2 = pd.DataFrame({'A': [1, 2], 'C': [5, 6]})
merged = pd.merge(df1, df2, on='A')

# Export results
# df.to_csv('output.csv', index=False)
# df.to_excel('output.xlsx', index=False)

print("Monthly Sales Summary:")
print(monthly_sales)
print("\nRegional Analysis:")
print(regional_analysis)
```

### 🎭 **ASCII Art Demo**

```
    📊 pandas DataFrame
    
    ┌─────────┬─────┬──────────┬────────┐
    │  Name   │ Age │   City   │ Salary │
    ├─────────┼─────┼──────────┼────────┤
    │  Alice  │ 25  │   NYC    │ 70000  │
    │   Bob   │ 30  │   LA     │ 80000  │
    │ Charlie │ 35  │ Chicago  │ 90000  │
    │  Diana  │ 28  │ Boston   │ 75000  │
    └─────────┴─────┴──────────┴────────┘
    
         Filter → Group → Analyze → Export
```

---

## 🚀 Quick Start Examples

<div align="center">

```
    ┌─────────────────────────────────────────┐
    │         🚀 Ready-to-Use Examples        │
    │                                         │
    │  📁 Projects  🛠️ Templates  💡 Ideas    │
    └─────────────────────────────────────────┘
```

</div>

### 🌐 **Web Scraper with requests + pandas**

```python
import requests
import pandas as pd
from pathlib import Path

def scrape_github_repos(username):
    """Scrape GitHub repositories for a user."""
    url = f"https://api.github.com/users/{username}/repos"
    response = requests.get(url)
    
    if response.status_code == 200:
        repos = response.json()
        data = [{
            'name': repo['name'],
            'stars': repo['stargazers_count'],
            'language': repo['language'],
            'created': repo['created_at'][:10]
        } for repo in repos]
        
        df = pd.DataFrame(data)
        
        # Save to CSV
        output_path = Path(f'{username}_repos.csv')
        df.to_csv(output_path, index=False)
        
        return df
    else:
        raise Exception(f"Failed to fetch data: {response.status_code}")

# Usage
repos_df = scrape_github_repos('octocat')
print(repos_df.head())
```

### ⚡ **Async Data Processing**

```python
import asyncio
import aiohttp
import pandas as pd
from dataclasses import dataclass
from typing import List

@dataclass
class ApiResult:
    url: str
    status: int
    data: dict

async def fetch_multiple_apis(urls: List[str]) -> List[ApiResult]:
    """Fetch data from multiple APIs concurrently."""
    async def fetch_one(session, url):
        try:
            async with session.get(url) as response:
                data = await response.json()
                return ApiResult(url, response.status, data)
        except Exception as e:
            return ApiResult(url, 0, {'error': str(e)})
    
    async with aiohttp.ClientSession() as session:
        tasks = [fetch_one(session, url) for url in urls]
        results = await asyncio.gather(*tasks)
    
    return results

# Convert to DataFrame
async def analyze_api_data():
    urls = [
        'https://api.github.com/users/octocat',
        'https://api.github.com/users/defunkt',
        'https://api.github.com/users/mojombo'
    ]
    
    results = await fetch_multiple_apis(urls)
    
    # Extract data for analysis
    data = []
    for result in results:
        if result.status == 200 and 'error' not in result.data:
            data.append({
                'username': result.data['login'],
                'followers': result.data['followers'],
                'repos': result.data['public_repos'],
                'created': result.data['created_at'][:10]
            })
    
    df = pd.DataFrame(data)
    print(df)
    return df

# Run async function
# asyncio.run(analyze_api_data())
```

### 📊 **Configuration-Driven Analytics**

```python
from dataclasses import dataclass, field
from pathlib import Path
from dotenv import load_dotenv
import pandas as pd
import numpy as np
import os

load_dotenv()

@dataclass
class AnalyticsConfig:
    data_source: str = field(default_factory=lambda: os.getenv('DATA_SOURCE', 'data.csv'))
    output_dir: Path = field(default_factory=lambda: Path(os.getenv('OUTPUT_DIR', './output')))
    sample_size: int = field(default_factory=lambda: int(os.getenv('SAMPLE_SIZE', '1000')))
    random_seed: int = field(default_factory=lambda: int(os.getenv('RANDOM_SEED', '42')))
    
    def __post_init__(self):
        self.output_dir.mkdir(exist_ok=True)
        np.random.seed(self.random_seed)

class DataAnalyzer:
    def __init__(self, config: AnalyticsConfig):
        self.config = config
        self.data = None
    
    def load_data(self):
        """Load data with various fallbacks."""
        try:
            if self.config.data_source.endswith('.csv'):
                self.data = pd.read_csv(self.config.data_source)
            elif self.config.data_source.endswith('.json'):
                self.data = pd.read_json(self.config.data_source)
            else:
                # Generate sample data if no file found
                self.data = self._generate_sample_data()
        except FileNotFoundError:
            print(f"File {self.config.data_source} not found. Generating sample data.")
            self.data = self._generate_sample_data()
    
    def _generate_sample_data(self):
        """Generate sample data for demonstration."""
        return pd.DataFrame({
            'date': pd.date_range('2023-01-01', periods=self.config.sample_size),
            'value': np.random.normal(100, 15, self.config.sample_size),
            'category': np.random.choice(['A', 'B', 'C'], self.config.sample_size)
        })
    
    def analyze(self):
        """Perform analysis and save results."""
        if self.data is None:
            self.load_data()
        
        # Analysis
        summary = self.data.describe()
        category_stats = self.data.groupby('category')['value'].agg(['mean', 'std', 'count'])
        
        # Save results
        summary.to_csv(self.config.output_dir / 'summary.csv')
        category_stats.to_csv(self.config.output_dir / 'category_analysis.csv')
        
        print("Analysis completed!")
        print(f"Results saved to: {self.config.output_dir}")
        
        return summary, category_stats

# Usage
config = AnalyticsConfig()
analyzer = DataAnalyzer(config)
summary, category_stats = analyzer.analyze()
```

---

## 💡 Best Practices

<div align="center">

```
    ┌─────────────────────────────────────────┐
    │         💡 Best Practices               │
    │                                         │
    │  🎯 Tips  🛡️ Security  ⚡ Performance   │
    └─────────────────────────────────────────┘
```

</div>

### 🛡️ **Security Best Practices**

```python
# ✅ DO: Use environment variables for secrets
from dotenv import load_dotenv
import os

load_dotenv()
API_KEY = os.getenv('API_KEY')
if not API_KEY:
    raise ValueError("API_KEY not found in environment variables")

# ❌ DON'T: Hardcode secrets
API_KEY = 'sk-1234567890abcdef'  # Never do this!

# ✅ DO: Validate and sanitize inputs
def safe_request(url: str) -> dict:
    if not url.startswith(('http://', 'https://')):
        raise ValueError("Invalid URL scheme")
    
    response = requests.get(url, timeout=10)
    response.raise_for_status()
    return response.json()
```

### ⚡ **Performance Best Practices**

```python
import pandas as pd
import numpy as np

# ✅ DO: Use vectorized operations
# Fast
df['new_column'] = df['column1'] * df['column2']

# ❌ DON'T: Use loops for element-wise operations
# Slow
# for i in range(len(df)):
#     df.loc[i, 'new_column'] = df.loc[i, 'column1'] * df.loc[i, 'column2']

# ✅ DO: Use async for I/O operations
async def fetch_multiple_urls(urls):
    async with aiohttp.ClientSession() as session:
        tasks = [session.get(url) for url in urls]
        responses = await asyncio.gather(*tasks)
    return responses

# ✅ DO: Use appropriate data types
df['category'] = df['category'].astype('category')  # Save memory
df['is_active'] = df['is_active'].astype('bool')
```

### 🎯 **Code Organization Best Practices**

```python
from dataclasses import dataclass
from pathlib import Path
from typing import Optional, List
import logging

# ✅ DO: Use type hints
@dataclass
class DataProcessor:
    input_file: Path
    output_dir: Path
    chunk_size: int = 1000
    
    def process(self) -> Optional[pd.DataFrame]:
        """Process data in chunks for memory efficiency."""
        try:
            chunks = []
            for chunk in pd.read_csv(self.input_file, chunksize=self.chunk_size):
                processed_chunk = self._process_chunk(chunk)
                chunks.append(processed_chunk)
            
            result = pd.concat(chunks, ignore_index=True)
            return result
            
        except Exception as e:
            logging.error(f"Processing failed: {e}")
            return None
    
    def _process_chunk(self, chunk: pd.DataFrame) -> pd.DataFrame:
        # Process individual chunk
        return chunk.dropna()

# ✅ DO: Use context managers
def safe_file_operation(file_path: Path) -> str:
    with open(file_path, 'r') as f:
        content = f.read()
    return content

# ✅ DO: Handle errors gracefully
def robust_api_call(url: str, retries: int = 3) -> Optional[dict]:
    for attempt in range(retries):
        try:
            response = requests.get(url, timeout=10)
            response.raise_for_status()
            return response.json()
        except requests.RequestException as e:
            if attempt == retries - 1:
                logging.error(f"Final attempt failed: {e}")
                return None
            logging.warning(f"Attempt {attempt + 1} failed, retrying...")
            time.sleep(2 ** attempt)  # Exponential backoff
```

### 📁 **Project Structure**

```
my_project/
├── 📄 .env                    # Environment variables
├── 📄 .env.example           # Example environment file
├── 📄 .gitignore             # Git ignore patterns
├── 📄 requirements.txt       # Dependencies
├── 📄 README.md              # Project documentation
├── 📁 src/
│   ├── 📄 __init__.py
│   ├── 📄 config.py          # Configuration management
│   ├── 📄 models.py          # Data models (dataclasses)
│   ├── 📄 api_client.py      # API interactions (requests)
│   ├── 📄 data_processor.py  # Data processing (pandas/numpy)
│   └── 📄 async_tasks.py     # Async operations (asyncio)
├── 📁 data/
│   ├── 📄 raw/              # Raw data files
│   └── 📄 processed/        # Processed data files
├── 📁 tests/
│   ├── 📄 __init__.py
│   ├── 📄 test_models.py
│   └── 📄 test_api_client.py
└── 📁 scripts/
    ├── 📄 data_migration.py
    └── 📄 daily_report.py
```

---

## 🔗 Resources

<div align="center">

```
    ┌─────────────────────────────────────────┐
    │         🔗 Additional Resources         │
    │                                         │
    │  📚 Docs  🎓 Tutorials  🌟 Examples     │
    └─────────────────────────────────────────┘
```

</div>

### 📚 **Official Documentation**

- **requests**: [docs.python-requests.org](https://docs.python-requests.org/en/latest/)[1]
- **pathlib**: [docs.python.org/3/library/pathlib.html](https://docs.python.org/3/library/pathlib.html)[2]
- **asyncio**: [docs.python.org/3/library/asyncio.html](https://docs.python.org/3/library/asyncio.html)[3]
- **dataclasses**: [docs.python.org/3/library/dataclasses.html](https://docs.python.org/3/library/dataclasses.html)[4]
- **python-dotenv**: [pypi.org/project/python-dotenv/](https://pypi.org/project/python-dotenv/)[5]
- **numpy**: [numpy.org/doc/stable/](https://numpy.org/doc/stable/)[6]
- **pandas**: [pandas.pydata.org/docs/](https://pandas.pydata.org/docs/)[7]

### 🛠️ **Installation Commands**

```bash
# Individual packages
pip install requests
pip install python-dotenv
pip install numpy
pip install pandas

# All at once
pip install requests pathlib python-dotenv numpy pandas

# With async support
pip install aiohttp aiofiles

# Development dependencies
pip install pytest black flake8 mypy
```

### 🎯 **Quick Reference Cheat Sheet**

```python
# requests - HTTP made simple
import requests
r = requests.get('https://api.example.com/data')
data = r.json()

# pathlib - Modern path handling  
from pathlib import Path
file = Path('data.txt')
content = file.read_text()

# asyncio - Async programming
import asyncio
async def main():
    await asyncio.sleep(1)
asyncio.run(main())

# dataclasses - Less boilerplate
from dataclasses import dataclass
@dataclass
class User:
    name: str
    age: int

# python-dotenv - Environment config
from dotenv import load_dotenv
load_dotenv()

# numpy - Numerical computing
import numpy as np
arr = np.array([1, 2, 3])
result = np.sum(arr)

# pandas - Data analysis
import pandas as pd
df = pd.DataFrame({'A': [1, 2], 'B': [3, 4]})
```

---

<div align="center">

```
    ╔═══════════════════════════════════════════╗
    ║               🎉 Happy Coding! 🎉         ║
    ║                                           ║
    ║    Master these packages and unlock       ║
    ║       the full power of Python! 🐍        ║
    ╚═══════════════════════════════════════════╝
```

**Built with ❤️ for Python developers**

</div>

---

*Last updated: October 2025*