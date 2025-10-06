# 🐍 Python Decorators: The Complete Interactive Guide

[![Python Decorators](https://img.shields.io/badge/Python-Decorators-blue?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
![Level](https://img.shields.io/badge/Level-Beginner%20to%20Advanced-orange?style=for-the-badge)


---

```
╔════════════════════════════════════════════════════════════════════════════╗
║                                                                            ║
║    ██████╗ ██╗   ██╗████████╗██╗  ██╗ ██████╗ ███╗    ██╗                  ║
║    ██╔══██╗╚██╗ ██╔╝╚══██╔══╝██║  ██║██╔═══██╗█████╗  ██║                  ║
║    ██████╔╝ ╚████╔╝    ██║   ███████║██║   ██║██╔████╗██║                  ║
║    ██╔═══╝   ╚██╔╝     ██║   ██╔══██║██║   ██║██║ ╚█████║                  ║
║    ██║        ██║      ██║   ██║  ██║╚██████╔╝██║   ╚███║                  ║
║    ╚═╝        ╚═╝      ╚═╝   ╚═╝  ╚═╝ ╚═════╝ ╚═╝     ╚═╝                  ║
║                                                                            ║
║              🎭 DECORATORS: METAPROGRAMMING MAGIC 🎭                       ║
║                                                                            ║
║    "A decorator takes in a function, adds some functionality               ║
║     and returns it – it's function enhancement without surgery!"           ║
║                                                                            ║
╚════════════════════════════════════════════════════════════════════════════╝
```

## 📚 Table of Contents

- [🎯 What Are Python Decorators?](#what-are-python-decorators)
- [🧠 Core Concepts & Mental Models](#core-concepts--mental-models)
- [🔧 Basic Decorator Patterns](#basic-decorator-patterns)
- [⚡ Decorators with Arguments](#decorators-with-arguments)
- [🏗️ Class-Based Decorators](#class-based-decorators)
- [🌟 Built-in Decorators](#built-in-decorators)
- [🔗 Chaining Multiple Decorators](#chaining-multiple-decorators)
- [🚀 Advanced Techniques](#advanced-techniques)
- [💼 Real-World Use Cases](#real-world-use-cases)
- [🎯 Best Practices & Performance](#best-practices--performance)
- [🧪 Interactive Exercises](#interactive-exercises)

---

## 🎯 What Are Python Decorators?

```
    ┌─────────────────────────────────────────────┐
    │               DECORATOR CONCEPT             │
    └─────────────────────────────────────────────┘
    
    🎭 Original Function     ➜    🎪 Enhanced Function
    ┌─────────────────┐           ┌─────────────────┐
    │  def my_func(): │    @deco  │ Wrapper around  │
    │    return "Hi"  │    ====>  │   my_func()     │
    │                 │           │ + Extra Magic!  │
    └─────────────────┘           └─────────────────┘
```

**Python decorators** are a powerful metaprogramming tool that allows you to **modify or extend the behavior of functions** without changing their actual code. Think of them as "function wrappers" that add extra functionality.

### 🧩 Key Characteristics:
- **Higher-order functions**: Take functions as arguments and return functions
- **Syntactic sugar**: Clean `@decorator` syntax for easy application  
- **Non-invasive**: Don't modify original function source code
- **Reusable**: Can be applied to multiple functions
- **Composable**: Multiple decorators can be chained together

---

## 🧠 Core Concepts & Mental Models

### 💡 Functions as First-Class Objects

In Python, **functions are objects**! This is the foundation that makes decorators possible:

```python
def greet():
    return "Hello World!"

# Functions can be assigned to variables
my_func = greet
print(my_func())  # Output: Hello World!

# Functions can be passed as arguments
def call_func(func):
    return func()

result = call_func(greet)  # Passing function as argument
print(result)  # Output: Hello World!
```

### 🎭 The Decorator Mental Model

```
    BEFORE DECORATION:
    ┌─────────────────┐
    │   function()    │  ➜  Returns: "result"
    └─────────────────┘
    
    AFTER DECORATION:
    ┌─────────────────┐
    │   @decorator    │
    │   function()    │  ➜  Returns: enhanced "result"
    └─────────────────┘
    
    UNDER THE HOOD:
    ┌───────────────────────────────────────────────┐
    │              wrapper_function                 │
    │  ┌─────────────────────────────────────────┐  │
    │  │         # Before original function      │  │
    │  │         result = original_function()    │  │  
    │  │         # After original function       │  │
    │  │         return enhanced_result          │  │
    │  └─────────────────────────────────────────┘  │
    └───────────────────────────────────────────────┘
```

### 🔄 Decorator Execution Flow

```
    Step 1: Define decorator function
           ⬇
    Step 2: Apply @decorator syntax  
           ⬇
    Step 3: Python replaces original function with wrapper
           ⬇
    Step 4: When function called, wrapper executes instead
```

---

## 🔧 Basic Decorator Patterns

### 🎯 Simple Function Decorator

```python
def my_decorator(func):
    """
    Basic decorator pattern - the foundation of all decorators
    """
    def wrapper():
        print("🎭 Something before the function")
        func()  # Call original function
        print("🎭 Something after the function")
    return wrapper

@my_decorator
def say_hello():
    print("👋 Hello!")

# Usage
say_hello()

"""
Output:
🎭 Something before the function  
👋 Hello!
🎭 Something after the function
"""
```

### 🔄 The Manual Approach (Without @ Syntax)

```python
def timer_decorator(func):
    def wrapper():
        import time
        start = time.time()
        result = func()
        end = time.time()
        print(f"⏱️ Function took {end - start:.4f} seconds")
        return result
    return wrapper

def slow_function():
    import time
    time.sleep(1)
    return "Task completed!"

# Manual decoration (equivalent to @timer_decorator)
slow_function = timer_decorator(slow_function)
result = slow_function()
```

### 📦 Handling Function Arguments with *args and **kwargs

```python
def debug_calls(func):
    """
    Decorator that logs function calls with their arguments
    """
    from functools import wraps
    
    @wraps(func)  # Preserves original function metadata
    def wrapper(*args, **kwargs):
        print(f"🐛 Calling {func.__name__}")
        print(f"   📥 Args: {args}")
        print(f"   📋 Kwargs: {kwargs}")
        
        result = func(*args, **kwargs)
        
        print(f"   📤 Result: {result}")
        return result
    return wrapper

@debug_calls
def calculate_area(length, width, unit="meters"):
    return f"{length * width} square {unit}"

# Test it
area = calculate_area(5, 3, unit="feet")

"""
Output:
🐛 Calling calculate_area
   📥 Args: (5, 3)  
   📋 Kwargs: {'unit': 'feet'}
   📤 Result: 15 square feet
"""
```

### 🔧 functools.wraps - Preserving Function Identity

```python
from functools import wraps

def better_decorator(func):
    @wraps(func)  # This preserves original function's metadata
    def wrapper(*args, **kwargs):
        """Wrapper function docstring"""
        print(f"🎯 Enhancing {func.__name__}")
        return func(*args, **kwargs)
    return wrapper

@better_decorator  
def important_function():
    """This function does important work"""
    return "Important result"

# Check preserved metadata
print(f"Function name: {important_function.__name__}")
print(f"Function doc: {important_function.__doc__}")
print(f"Function module: {important_function.__module__}")
```

---

## ⚡ Decorators with Arguments

### 🎛️ Decorator Factory Pattern

When you need to pass parameters to your decorators, you create a **decorator factory** - a function that returns a decorator:

```python
def repeat(times):
    """
    Decorator factory that creates a decorator to repeat function calls
    
    Usage: @repeat(3)
    """
    def decorator(func):
        from functools import wraps
        
        @wraps(func)
        def wrapper(*args, **kwargs):
            results = []
            for i in range(times):
                print(f"🔄 Execution #{i + 1}")
                result = func(*args, **kwargs)
                results.append(result)
            return results
        return wrapper
    return decorator

@repeat(times=3)
def greet_user(name):
    return f"Hello, {name}!"

# Test it
messages = greet_user("Alice")
print(messages)

"""
Output:
🔄 Execution #1
🔄 Execution #2  
🔄 Execution #3
['Hello, Alice!', 'Hello, Alice!', 'Hello, Alice!']
"""
```

### 🎚️ Flexible Decorator with Optional Arguments

```python
def smart_cache(maxsize=128, ttl=None):
    """
    Advanced caching decorator with size limit and time-to-live
    
    Args:
        maxsize: Maximum cache size (default: 128)
        ttl: Time-to-live in seconds (default: None = no expiry)
    """
    def decorator(func):
        import time
        from functools import wraps
        
        cache = {}
        access_times = {} if ttl else None
        
        @wraps(func)
        def wrapper(*args, **kwargs):
            # Create cache key
            key = str(args) + str(sorted(kwargs.items()))
            
            # Check TTL expiry
            if ttl and key in access_times:
                if time.time() - access_times[key] > ttl:
                    cache.pop(key, None)
                    access_times.pop(key, None)
            
            # Return cached result if available
            if key in cache:
                print(f"💾 Cache HIT for {func.__name__}")
                return cache[key]
            
            # Compute and cache result
            print(f"🔄 Computing {func.__name__}")
            result = func(*args, **kwargs)
            
            # Manage cache size
            if len(cache) >= maxsize:
                oldest_key = next(iter(cache))
                cache.pop(oldest_key)
                if access_times:
                    access_times.pop(oldest_key, None)
            
            cache[key] = result
            if ttl:
                access_times[key] = time.time()
                
            return result
        
        # Add cache management methods
        wrapper.cache_clear = lambda: cache.clear()
        wrapper.cache_info = lambda: {
            'size': len(cache), 
            'maxsize': maxsize,
            'ttl': ttl
        }
        
        return wrapper
    return decorator

@smart_cache(maxsize=3, ttl=60)  # Cache max 3 items for 60 seconds
def expensive_calculation(n):
    """Simulates expensive computation"""
    import time
    time.sleep(0.1)  # Simulate work
    return n ** 2

# Test the cache
print(expensive_calculation(5))  # Computed
print(expensive_calculation(5))  # Cached
print(expensive_calculation.cache_info())
```

### 🎪 Decorator with Conditional Arguments

```python
def conditional_decorator(condition=True, message="Default"):
    """
    Decorator that conditionally applies functionality
    """
    def decorator(func):
        from functools import wraps
        
        @wraps(func)
        def wrapper(*args, **kwargs):
            if condition:
                print(f"🎯 {message}")
                result = func(*args, **kwargs)
                print("✅ Function completed")
                return result
            else:
                print("⏭️ Decorator inactive")
                return func(*args, **kwargs)
        return wrapper
    return decorator

# Different usage patterns
@conditional_decorator()  # Default parameters
def func1():
    return "Result 1"

@conditional_decorator(condition=False)  # Disabled
def func2():
    return "Result 2"

@conditional_decorator(condition=True, message="Custom message!")
def func3():
    return "Result 3"
```

---

## 🏗️ Class-Based Decorators

### 🏛️ Basic Class Decorator

```python
class CallCounter:
    """
    Class-based decorator to count function calls
    """
    def __init__(self, func):
        self.func = func
        self.count = 0
        
        # Preserve function metadata
        from functools import update_wrapper
        update_wrapper(self, func)
    
    def __call__(self, *args, **kwargs):
        self.count += 1
        print(f"📊 Call #{self.count} to {self.func.__name__}")
        return self.func(*args, **kwargs)
    
    def reset_count(self):
        """Reset the call counter"""
        self.count = 0

@CallCounter
def greet(name):
    return f"Hello, {name}!"

# Usage
print(greet("Alice"))    # Call #1
print(greet("Bob"))      # Call #2
print(f"Total calls: {greet.count}")
greet.reset_count()
print(f"After reset: {greet.count}")
```

### 🎛️ Parameterized Class Decorators

```python
class RateLimit:
    """
    Class-based decorator for rate limiting function calls
    """
    def __init__(self, max_calls=5, window_seconds=60):
        self.max_calls = max_calls
        self.window_seconds = window_seconds
        self.calls = []
    
    def __call__(self, func):
        from functools import wraps
        import time
        
        @wraps(func)
        def wrapper(*args, **kwargs):
            now = time.time()
            
            # Clean old calls outside window
            self.calls = [call_time for call_time in self.calls 
                         if now - call_time < self.window_seconds]
            
            # Check rate limit
            if len(self.calls) >= self.max_calls:
                raise Exception(
                    f"🚫 Rate limit exceeded! "
                    f"Max {self.max_calls} calls per {self.window_seconds}s"
                )
            
            # Record this call and execute
            self.calls.append(now)
            print(f"⚡ Call allowed ({len(self.calls)}/{self.max_calls})")
            return func(*args, **kwargs)
        
        wrapper.get_stats = lambda: {
            'calls_in_window': len(self.calls),
            'max_calls': self.max_calls,
            'window_seconds': self.window_seconds
        }
        
        return wrapper

@RateLimit(max_calls=3, window_seconds=10)
def api_call(endpoint):
    return f"📡 Calling {endpoint}"

# Test rate limiting
try:
    for i in range(5):
        print(api_call(f"/api/endpoint{i}"))
except Exception as e:
    print(f"Error: {e}")
```

### 🧩 Advanced Class Decorator with State Management

```python
class StatefulDecorator:
    """
    Advanced class decorator that maintains state across calls
    """
    def __init__(self, track_history=True, max_history=100):
        self.track_history = track_history
        self.max_history = max_history
        self.history = []
        self.statistics = {
            'total_calls': 0,
            'total_runtime': 0,
            'average_runtime': 0,
            'last_result': None
        }
    
    def __call__(self, func):
        from functools import wraps
        import time
        
        @wraps(func)
        def wrapper(*args, **kwargs):
            start_time = time.time()
            
            try:
                result = func(*args, **kwargs)
                success = True
                error = None
            except Exception as e:
                result = None
                success = False
                error = str(e)
                raise  # Re-raise the exception
            finally:
                end_time = time.time()
                runtime = end_time - start_time
                
                # Update statistics
                self.statistics['total_calls'] += 1
                self.statistics['total_runtime'] += runtime
                self.statistics['average_runtime'] = (
                    self.statistics['total_runtime'] / 
                    self.statistics['total_calls']
                )
                self.statistics['last_result'] = result
                
                # Track history if enabled
                if self.track_history:
                    call_record = {
                        'timestamp': end_time,
                        'args': args,
                        'kwargs': kwargs,
                        'result': result,
                        'runtime': runtime,
                        'success': success,
                        'error': error
                    }
                    
                    self.history.append(call_record)
                    
                    # Maintain max history size
                    if len(self.history) > self.max_history:
                        self.history.pop(0)
            
            return result
        
        # Add utility methods
        wrapper.get_statistics = lambda: self.statistics.copy()
        wrapper.get_history = lambda: self.history.copy()
        wrapper.clear_history = lambda: self.history.clear()
        wrapper.get_last_calls = lambda n=5: self.history[-n:]
        
        return wrapper

@StatefulDecorator(track_history=True, max_history=50)
def data_processor(data, transform_type="normalize"):
    """Example function that processes data"""
    import time
    time.sleep(0.01)  # Simulate processing time
    
    if transform_type == "normalize":
        return [x / max(data) if max(data) != 0 else 0 for x in data]
    elif transform_type == "square":
        return [x ** 2 for x in data]
    else:
        raise ValueError(f"Unknown transform: {transform_type}")

# Test the advanced decorator
data_processor([1, 2, 3, 4, 5])
data_processor([10, 20, 30], transform_type="square")
data_processor([0, 1, 2])

print("📊 Statistics:", data_processor.get_statistics())
print("📋 Last 2 calls:", data_processor.get_last_calls(2))
```

---

## 🌟 Built-in Decorators

### 🏛️ @staticmethod and @classmethod

```python
class MathUtils:
    """Demonstration of built-in method decorators"""
    
    class_variable = "Math Utility Class"
    
    def __init__(self, name):
        self.name = name
    
    @staticmethod
    def add_numbers(a, b):
        """
        Static method - no access to instance or class
        Can be called on class or instance
        """
        return a + b
    
    @classmethod  
    def create_calculator(cls, name):
        """
        Class method - receives class as first argument
        Used for alternative constructors
        """
        print(f"Creating {cls.__name__} instance: {name}")
        return cls(name)
    
    @classmethod
    def get_class_info(cls):
        """Access class variables"""
        return cls.class_variable
    
    def multiply(self, a, b):
        """Regular instance method"""
        return a * b

# Usage examples
math_utils = MathUtils("Calculator")

# Static method - no self or cls needed
print(MathUtils.add_numbers(5, 3))        # Called on class
print(math_utils.add_numbers(5, 3))       # Called on instance

# Class method - alternative constructor
new_calc = MathUtils.create_calculator("Scientific")
print(new_calc.name)

# Class method - accessing class variables
print(MathUtils.get_class_info())
```

### 🏠 @property - Creating Managed Attributes

```python
class SmartTemperature:
    """Demonstrates @property for computed and validated attributes"""
    
    def __init__(self, celsius=0):
        self._celsius = celsius
        self._conversion_count = 0
    
    @property
    def celsius(self):
        """Getter for celsius temperature"""
        return self._celsius
    
    @celsius.setter  
    def celsius(self, value):
        """Setter with validation"""
        if not isinstance(value, (int, float)):
            raise TypeError("Temperature must be a number")
        if value < -273.15:  # Absolute zero
            raise ValueError("Temperature cannot be below absolute zero")
        
        self._celsius = value
        print(f"🌡️ Temperature set to {value}°C")
    
    @property
    def fahrenheit(self):
        """Computed property - Fahrenheit from Celsius"""
        self._conversion_count += 1
        return (self._celsius * 9/5) + 32
    
    @property
    def kelvin(self):
        """Computed property - Kelvin from Celsius"""
        self._conversion_count += 1
        return self._celsius + 273.15
    
    @property
    def conversion_stats(self):
        """Read-only property showing usage statistics"""
        return {
            'conversions_performed': self._conversion_count,
            'current_celsius': self._celsius
        }

# Usage
temp = SmartTemperature(25)
print(f"🌡️ {temp.celsius}°C = {temp.fahrenheit}°F = {temp.kelvin}K")

temp.celsius = 0  # Using setter with validation  
print(f"🌡️ Freezing point: {temp.fahrenheit}°F")

print(f"📊 Stats: {temp.conversion_stats}")

# This will raise an error:
# temp.celsius = -300  # Below absolute zero
```

### 💾 @functools.lru_cache - Built-in Memoization

```python
import functools
import time

class FibonacciCalculator:
    """Demonstrates built-in caching decorators"""
    
    @staticmethod
    def fibonacci_slow(n):
        """Slow recursive Fibonacci without caching"""
        if n < 2:
            return n
        return (FibonacciCalculator.fibonacci_slow(n-1) + 
                FibonacciCalculator.fibonacci_slow(n-2))
    
    @staticmethod
    @functools.lru_cache(maxsize=None)  # Unlimited cache
    def fibonacci_fast(n):
        """Fast Fibonacci with LRU caching"""
        if n < 2:
            return n
        return (FibonacciCalculator.fibonacci_fast(n-1) + 
                FibonacciCalculator.fibonacci_fast(n-2))
    
    @staticmethod
    @functools.cache  # Python 3.9+ - unlimited LRU cache
    def fibonacci_newest(n):
        """Fibonacci with newest cache decorator"""
        if n < 2:
            return n
        return (FibonacciCalculator.fibonacci_newest(n-1) + 
                FibonacciCalculator.fibonacci_newest(n-2))

def benchmark_fibonacci():
    """Compare performance of cached vs uncached"""
    
    # Test slow version
    start = time.time()
    result_slow = FibonacciCalculator.fibonacci_slow(30)
    time_slow = time.time() - start
    
    # Test fast version  
    start = time.time()
    result_fast = FibonacciCalculator.fibonacci_fast(30)
    time_fast = time.time() - start
    
    print(f"🐌 Slow fibonacci(30): {result_slow} in {time_slow:.4f}s")
    print(f"⚡ Fast fibonacci(30): {result_fast} in {time_fast:.4f}s") 
    print(f"🚀 Speedup: {time_slow/time_fast:.1f}x faster!")
    
    # Show cache statistics
    print(f"📊 Cache info: {FibonacciCalculator.fibonacci_fast.cache_info()}")

benchmark_fibonacci()
```

---

## 🔗 Chaining Multiple Decorators

### 🔄 Decorator Execution Order

When multiple decorators are applied, they execute in a **"bottom-up"** order during decoration, but **"outside-in"** order during execution:

```python
def decorator_a(func):
    print("🅰️ Decorator A: Decorating function")
    def wrapper(*args, **kwargs):
        print("🅰️ Decorator A: Before function")
        result = func(*args, **kwargs)
        print("🅰️ Decorator A: After function")
        return result
    return wrapper

def decorator_b(func):
    print("🅱️ Decorator B: Decorating function")
    def wrapper(*args, **kwargs):
        print("🅱️ Decorator B: Before function")
        result = func(*args, **kwargs)
        print("🅱️ Decorator B: After function")
        return result
    return wrapper

def decorator_c(func):
    print("🅾️ Decorator C: Decorating function")
    def wrapper(*args, **kwargs):
        print("🅾️ Decorator C: Before function")
        result = func(*args, **kwargs)
        print("🅾️ Decorator C: After function")
        return result
    return wrapper

@decorator_a      # Applied third (outermost)
@decorator_b      # Applied second  
@decorator_c      # Applied first (closest to function)
def my_function():
    print("🎯 Original function executing")
    return "Function result"

"""
Decoration order (bottom-up):
1. decorator_c wraps my_function
2. decorator_b wraps (decorator_c(my_function))
3. decorator_a wraps (decorator_b(decorator_c(my_function)))

Equivalent to:
my_function = decorator_a(decorator_b(decorator_c(my_function)))
"""

print("=" * 50)
print("🚀 Calling decorated function:")
result = my_function()
print(f"📤 Final result: {result}")
```

### 🎪 Practical Decorator Chaining Example

```python
import time
import functools
from datetime import datetime

def timer(func):
    """Measures execution time"""
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        duration = time.time() - start
        print(f"⏱️ {func.__name__} took {duration:.4f} seconds")
        return result
    return wrapper

def logger(func):
    """Logs function calls"""
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        timestamp = datetime.now().strftime("%H:%M:%S")
        print(f"📝 [{timestamp}] Calling {func.__name__} with args={args}")
        result = func(*args, **kwargs)
        print(f"📝 [{timestamp}] {func.__name__} returned: {result}")
        return result
    return wrapper

def validate_positive(func):
    """Validates that all arguments are positive numbers"""
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        # Check positional arguments
        for i, arg in enumerate(args):
            if isinstance(arg, (int, float)) and arg <= 0:
                raise ValueError(f"❌ Argument {i+1} must be positive, got {arg}")
        
        # Check keyword arguments  
        for key, value in kwargs.items():
            if isinstance(value, (int, float)) and value <= 0:
                raise ValueError(f"❌ {key} must be positive, got {value}")
        
        print("✅ All arguments validated as positive")
        return func(*args, **kwargs)
    return wrapper

def retry_on_failure(max_attempts=3):
    """Retry decorator with exponential backoff"""
    def decorator(func):
        @functools.wraps(func)
        def wrapper(*args, **kwargs):
            for attempt in range(max_attempts):
                try:
                    return func(*args, **kwargs)
                except Exception as e:
                    if attempt == max_attempts - 1:
                        print(f"❌ Final attempt failed: {e}")
                        raise
                    
                    wait_time = 2 ** attempt  # Exponential backoff
                    print(f"⚠️ Attempt {attempt + 1} failed: {e}")
                    print(f"🔄 Retrying in {wait_time} seconds...")
                    time.sleep(wait_time)
        return wrapper
    return decorator

# Apply multiple decorators
@timer                          # Outermost: measure total time
@logger                         # Log all attempts  
@retry_on_failure(max_attempts=2) # Retry on failure
@validate_positive              # Innermost: validate inputs first
def unreliable_calculation(x, y, failure_rate=0.3):
    """
    Simulates an unreliable calculation that might fail
    """
    import random
    
    # Simulate random failures
    if random.random() < failure_rate:
        raise Exception(f"💥 Random failure in calculation")
    
    # Simulate some processing time
    time.sleep(0.1) 
    
    result = (x ** 2 + y ** 2) ** 0.5
    return round(result, 2)

# Test the chained decorators
try:
    result = unreliable_calculation(3, 4)
    print(f"🎉 Final result: {result}")
except Exception as e:
    print(f"💀 Operation failed completely: {e}")
```

### 🎯 Creating a Universal Decorator Chain

```python
class DecoratorChain:
    """
    Utility class for easily chaining multiple decorators
    """
    def __init__(self, *decorators):
        self.decorators = decorators
    
    def __call__(self, func):
        """Apply all decorators in reverse order"""
        for decorator in reversed(self.decorators):
            func = decorator(func)
        return func

# Create reusable decorator chains
api_endpoint_chain = DecoratorChain(
    timer,
    logger, 
    retry_on_failure(max_attempts=3),
    validate_positive
)

data_processing_chain = DecoratorChain(
    timer,
    functools.lru_cache(maxsize=128),
    logger
)

# Apply chains easily
@api_endpoint_chain
def process_user_data(user_id, score):
    """Simulated API endpoint"""
    return {"user_id": user_id, "processed_score": score * 1.5}

@data_processing_chain  
def expensive_computation(n):
    """Simulated expensive computation"""
    time.sleep(0.05)  # Simulate work
    return sum(i**2 for i in range(n))

# Test chains
result1 = process_user_data(123, 85.5)
result2 = expensive_computation(100)  # First call - computed
result3 = expensive_computation(100)  # Second call - cached
```

---

## 🚀 Advanced Techniques

### 🎯 Context-Aware Decorators

```python
import threading
from contextlib import contextmanager
from functools import wraps

class ContextDecorator:
    """
    Advanced decorator that's aware of execution context
    """
    def __init__(self, track_threading=True, track_recursion=True):
        self.track_threading = track_threading
        self.track_recursion = track_recursion
        self.call_stack = threading.local()  # Thread-local storage
    
    def __call__(self, func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            # Initialize thread-local data if needed
            if not hasattr(self.call_stack, 'stack'):
                self.call_stack.stack = []
            
            # Track context information
            context = {
                'function': func.__name__,
                'thread_id': threading.current_thread().ident,
                'recursion_depth': len(self.call_stack.stack),
                'is_recursive_call': func.__name__ in [
                    item['function'] for item in self.call_stack.stack
                ]
            }
            
            # Add to call stack
            self.call_stack.stack.append(context)
            
            try:
                # Display context info
                indent = "  " * context['recursion_depth']
                print(f"{indent}🎯 Entering {func.__name__}")
                
                if self.track_threading:
                    print(f"{indent}📍 Thread: {context['thread_id']}")
                
                if self.track_recursion and context['is_recursive_call']:
                    print(f"{indent}🔄 Recursive call (depth: {context['recursion_depth']})")
                
                # Execute function
                result = func(*args, **kwargs)
                
                print(f"{indent}✅ Exiting {func.__name__}")
                return result
                
            finally:
                # Remove from call stack
                self.call_stack.stack.pop()
        
        return wrapper

@ContextDecorator(track_threading=True, track_recursion=True)
def factorial(n):
    """Recursive function to demonstrate context tracking"""
    if n <= 1:
        return 1
    return n * factorial(n - 1)

@ContextDecorator(track_threading=True, track_recursion=True)  
def fibonacci(n):
    """Another recursive function"""
    if n < 2:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

# Test context awareness
print("🧮 Computing factorial(4):")
result = factorial(4)
print(f"Result: {result}\n")

print("🔢 Computing fibonacci(5):")  
result = fibonacci(5)
print(f"Result: {result}")
```

### 🏭 Decorator Factory with Configuration

```python
class ConfigurableDecorator:
    """
    Highly configurable decorator that can be customized for different use cases
    """
    
    def __init__(self, 
                 enable_timing=True,
                 enable_logging=True, 
                 enable_caching=False,
                 enable_validation=False,
                 cache_size=128,
                 log_format="simple"):
        
        self.config = {
            'timing': enable_timing,
            'logging': enable_logging,
            'caching': enable_caching,
            'validation': enable_validation,
            'cache_size': cache_size,
            'log_format': log_format
        }
        
        if enable_caching:
            self.cache = {}
    
    def __call__(self, func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            # Create cache key if caching is enabled
            if self.config['caching']:
                cache_key = str(args) + str(sorted(kwargs.items()))
                if cache_key in self.cache:
                    if self.config['logging']:
                        print(f"💾 Cache HIT for {func.__name__}")
                    return self.cache[cache_key]
            
            # Input validation if enabled
            if self.config['validation']:
                self._validate_inputs(*args, **kwargs)
            
            # Logging before execution
            if self.config['logging']:
                self._log_call(func, args, kwargs, 'start')
            
            # Timing
            import time
            start_time = time.time() if self.config['timing'] else None
            
            try:
                # Execute function
                result = func(*args, **kwargs)
                
                # Cache result if enabled
                if self.config['caching']:
                    # Manage cache size
                    if len(self.cache) >= self.config['cache_size']:
                        oldest_key = next(iter(self.cache))
                        del self.cache[oldest_key]
                    self.cache[cache_key] = result
                
                # Timing calculation
                if self.config['timing']:
                    duration = time.time() - start_time
                    print(f"⏱️ {func.__name__} executed in {duration:.4f}s")
                
                # Logging after execution
                if self.config['logging']:
                    self._log_call(func, args, kwargs, 'end', result)
                
                return result
                
            except Exception as e:
                if self.config['logging']:
                    self._log_call(func, args, kwargs, 'error', str(e))
                raise
        
        # Add utility methods
        if self.config['caching']:
            wrapper.cache_info = lambda: {
                'size': len(self.cache),
                'maxsize': self.config['cache_size'],
                'items': list(self.cache.keys())
            }
            wrapper.cache_clear = lambda: self.cache.clear()
        
        return wrapper
    
    def _validate_inputs(self, *args, **kwargs):
        """Basic input validation"""
        for i, arg in enumerate(args):
            if arg is None:
                raise ValueError(f"Argument {i} cannot be None")
    
    def _log_call(self, func, args, kwargs, phase, result=None):
        """Flexible logging based on configuration"""
        if self.config['log_format'] == 'simple':
            if phase == 'start':
                print(f"📞 Calling {func.__name__}")
            elif phase == 'end':
                print(f"✅ {func.__name__} completed")
            elif phase == 'error':
                print(f"❌ {func.__name__} failed: {result}")
                
        elif self.config['log_format'] == 'detailed':
            timestamp = time.strftime("%H:%M:%S")
            if phase == 'start':
                print(f"[{timestamp}] 📞 {func.__name__}({args}, {kwargs})")
            elif phase == 'end':
                print(f"[{timestamp}] ✅ {func.__name__} -> {result}")
            elif phase == 'error':
                print(f"[{timestamp}] ❌ {func.__name__} -> ERROR: {result}")

# Create different configurations
performance_decorator = ConfigurableDecorator(
    enable_timing=True,
    enable_logging=True,
    enable_caching=True,
    cache_size=50,
    log_format="detailed"
)

debug_decorator = ConfigurableDecorator(
    enable_timing=True,
    enable_logging=True,
    enable_validation=True,
    log_format="detailed"
)

simple_decorator = ConfigurableDecorator(
    enable_timing=False,
    enable_logging=True,
    log_format="simple"
)

# Apply different configurations
@performance_decorator
def expensive_operation(n):
    """Simulate expensive computation"""
    import time
    time.sleep(0.01)
    return sum(i**2 for i in range(n))

@debug_decorator
def data_processor(data, multiplier=1):
    """Process data with validation"""
    return [x * multiplier for x in data]

@simple_decorator  
def simple_function():
    """Basic function"""
    return "Hello, World!"

# Test different configurations
print("🚀 Performance decorated function:")
result1 = expensive_operation(100)  # Computed and cached
result2 = expensive_operation(100)  # Retrieved from cache

print("\n🐛 Debug decorated function:")
result3 = data_processor([1, 2, 3], multiplier=2)

print("\n📝 Simple decorated function:")
result4 = simple_function()
```

### 🔄 Async Decorator Support

```python
import asyncio
import time
from functools import wraps

def async_timer(func):
    """
    Decorator that works with both sync and async functions
    """
    if asyncio.iscoroutinefunction(func):
        @wraps(func)
        async def async_wrapper(*args, **kwargs):
            start = time.time()
            result = await func(*args, **kwargs)
            duration = time.time() - start
            print(f"⏰ Async {func.__name__} took {duration:.4f} seconds")
            return result
        return async_wrapper
    else:
        @wraps(func)
        def sync_wrapper(*args, **kwargs):
            start = time.time()
            result = func(*args, **kwargs)
            duration = time.time() - start
            print(f"⏰ Sync {func.__name__} took {duration:.4f} seconds")
            return result
        return sync_wrapper

def async_retry(max_attempts=3, delay=1):
    """
    Retry decorator for async functions
    """
    def decorator(func):
        @wraps(func)
        async def wrapper(*args, **kwargs):
            for attempt in range(max_attempts):
                try:
                    return await func(*args, **kwargs)
                except Exception as e:
                    if attempt == max_attempts - 1:
                        print(f"❌ All {max_attempts} attempts failed")
                        raise
                    
                    print(f"⚠️ Attempt {attempt + 1} failed: {e}")
                    print(f"🔄 Retrying in {delay} seconds...")
                    await asyncio.sleep(delay)
        return wrapper
    return decorator

# Apply to both sync and async functions
@async_timer
def sync_function():
    """Regular synchronous function"""
    time.sleep(0.1)
    return "Sync result"

@async_timer
async def async_function():
    """Asynchronous function"""
    await asyncio.sleep(0.1)
    return "Async result"

@async_retry(max_attempts=2, delay=0.5)
@async_timer
async def unreliable_async_function():
    """Async function that might fail"""
    import random
    if random.random() < 0.7:  # 70% chance of failure
        raise Exception("Random async failure")
    return "Success!"

# Test async decorators
async def test_async_decorators():
    print("🔄 Testing sync function:")
    result1 = sync_function()
    
    print("\n🔄 Testing async function:")
    result2 = await async_function()
    
    print("\n🔄 Testing unreliable async function:")
    try:
        result3 = await unreliable_async_function()
        print(f"✅ Success: {result3}")
    except Exception as e:
        print(f"💀 Final failure: {e}")

# Run async tests
if __name__ == "__main__":
    asyncio.run(test_async_decorators())
```

---

## 💼 Real-World Use Cases

### 🔐 Authentication & Authorization

```python
import jwt
from functools import wraps
from datetime import datetime, timedelta

class AuthenticationError(Exception):
    pass

class AuthorizationError(Exception):
    pass

# Mock user database
USERS = {
    "admin": {"password": "admin123", "roles": ["admin", "user"]},
    "user": {"password": "user123", "roles": ["user"]},
    "guest": {"password": "guest123", "roles": ["guest"]}
}

# Mock session storage
SESSIONS = {}

def login_required(func):
    """Decorator to require user authentication"""
    @wraps(func)
    def wrapper(*args, **kwargs):
        # Get token from kwargs or raise error
        token = kwargs.pop('auth_token', None)
        if not token:
            raise AuthenticationError("🚫 Authentication token required")
        
        # Validate token
        try:
            payload = jwt.decode(token, "secret", algorithms=["HS256"])
            username = payload['username']
            
            # Check if user exists and session is valid
            if username not in USERS:
                raise AuthenticationError("🚫 Invalid user")
                
            # Add user context to function
            kwargs['current_user'] = username
            kwargs['user_roles'] = USERS[username]['roles']
            
            return func(*args, **kwargs)
            
        except jwt.ExpiredSignatureError:
            raise AuthenticationError("🚫 Token has expired")
        except jwt.InvalidTokenError:
            raise AuthenticationError("🚫 Invalid token")
    
    return wrapper

def require_role(required_roles):
    """Decorator to require specific roles"""
    def decorator(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            user_roles = kwargs.get('user_roles', [])
            
            # Check if user has any of the required roles
            if not any(role in user_roles for role in required_roles):
                raise AuthorizationError(
                    f"🚫 Access denied. Required roles: {required_roles}, "
                    f"User roles: {user_roles}"
                )
            
            return func(*args, **kwargs)
        return wrapper
    return decorator

def audit_log(action):
    """Decorator to log user actions for auditing"""
    def decorator(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            start_time = datetime.now()
            current_user = kwargs.get('current_user', 'Anonymous')
            
            try:
                result = func(*args, **kwargs)
                
                # Log successful action
                print(f"📊 AUDIT: {start_time.isoformat()} - "
                      f"User '{current_user}' performed '{action}' - SUCCESS")
                
                return result
                
            except Exception as e:
                # Log failed action
                print(f"📊 AUDIT: {start_time.isoformat()} - "
                      f"User '{current_user}' attempted '{action}' - "
                      f"FAILED: {str(e)}")
                raise
        return wrapper
    return decorator

# Utility functions for authentication
def create_token(username):
    """Create JWT token for user"""
    payload = {
        'username': username,
        'exp': datetime.utcnow() + timedelta(hours=24)
    }
    return jwt.encode(payload, "secret", algorithm="HS256")

def authenticate_user(username, password):
    """Authenticate user and return token"""
    if username in USERS and USERS[username]['password'] == password:
        return create_token(username)
    raise AuthenticationError("Invalid username or password")

# Protected functions using decorators
@audit_log("view_sensitive_data")
@require_role(["admin", "user"])  
@login_required
def view_user_data(user_id, **kwargs):
    """View sensitive user data - requires authentication and proper role"""
    current_user = kwargs['current_user']
    print(f"👤 {current_user} viewing data for user {user_id}")
    return {"user_id": user_id, "data": "sensitive information"}

@audit_log("delete_user")
@require_role(["admin"])
@login_required  
def delete_user(user_id, **kwargs):
    """Delete user - admin only"""
    current_user = kwargs['current_user']
    print(f"🗑️ {current_user} deleting user {user_id}")
    return {"message": f"User {user_id} deleted successfully"}

@audit_log("read_public_data")
@login_required
def view_public_data(**kwargs):
    """View public data - any authenticated user"""
    current_user = kwargs['current_user']
    print(f"📰 {current_user} viewing public data")
    return {"data": "public information"}

# Demo the authentication system
def demo_auth_system():
    print("🔐 Authentication & Authorization Demo\n")
    
    try:
        # Login as different users
        admin_token = authenticate_user("admin", "admin123")
        user_token = authenticate_user("user", "user123")
        guest_token = authenticate_user("guest", "guest123")
        
        print("✅ All users authenticated successfully\n")
        
        # Test admin access
        print("👑 Testing admin access:")
        view_user_data(123, auth_token=admin_token)
        delete_user(456, auth_token=admin_token)
        
        print("\n👤 Testing regular user access:")
        view_user_data(123, auth_token=user_token)
        view_public_data(auth_token=user_token)
        
        print("\n🚫 Testing unauthorized access (guest trying to delete):")
        try:
            delete_user(789, auth_token=guest_token)
        except AuthorizationError as e:
            print(f"Expected error: {e}")
        
        print("\n🚫 Testing unauthenticated access:")
        try:
            view_user_data(123)  # No token provided
        except AuthenticationError as e:
            print(f"Expected error: {e}")
            
    except Exception as e:
        print(f"Demo error: {e}")

demo_auth_system()
```

### 📊 Performance Monitoring & Profiling

```python
import time
import psutil
import threading
from collections import defaultdict, deque
from functools import wraps
from datetime import datetime, timedelta

class PerformanceMonitor:
    """
    Comprehensive performance monitoring decorator
    """
    def __init__(self, track_memory=True, track_cpu=True, history_size=1000):
        self.track_memory = track_memory
        self.track_cpu = track_cpu
        self.history_size = history_size
        
        # Thread-safe storage for metrics
        self._lock = threading.Lock()
        self.metrics = defaultdict(lambda: {
            'call_count': 0,
            'total_time': 0,
            'avg_time': 0,
            'min_time': float('inf'),
            'max_time': 0,
            'memory_usage': deque(maxlen=history_size),
            'cpu_usage': deque(maxlen=history_size),
            'call_history': deque(maxlen=history_size),
            'error_count': 0,
            'last_called': None
        })
    
    def __call__(self, func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            start_time = time.time()
            
            # Get initial system metrics
            if self.track_memory:
                memory_before = psutil.Process().memory_info().rss / 1024 / 1024  # MB
            if self.track_cpu:
                cpu_before = psutil.cpu_percent()
            
            try:
                # Execute function
                result = func(*args, **kwargs)
                
                # Calculate execution metrics
                execution_time = time.time() - start_time
                
                # Get final system metrics
                if self.track_memory:
                    memory_after = psutil.Process().memory_info().rss / 1024 / 1024
                    memory_delta = memory_after - memory_before
                if self.track_cpu:
                    cpu_after = psutil.cpu_percent()
                
                # Update statistics thread-safely
                with self._lock:
                    metrics = self.metrics[func.__name__]
                    
                    # Update timing statistics
                    metrics['call_count'] += 1
                    metrics['total_time'] += execution_time
                    metrics['avg_time'] = metrics['total_time'] / metrics['call_count']
                    metrics['min_time'] = min(metrics['min_time'], execution_time)
                    metrics['max_time'] = max(metrics['max_time'], execution_time)
                    metrics['last_called'] = datetime.now()
                    
                    # Update system resource metrics
                    if self.track_memory:
                        metrics['memory_usage'].append({
                            'timestamp': datetime.now(),
                            'before': memory_before,
                            'after': memory_after,
                            'delta': memory_delta
                        })
                    
                    if self.track_cpu:
                        metrics['cpu_usage'].append({
                            'timestamp': datetime.now(),
                            'before': cpu_before,
                            'after': cpu_after
                        })
                    
                    # Record call details
                    metrics['call_history'].append({
                        'timestamp': datetime.now(),
                        'execution_time': execution_time,
                        'args_count': len(args),
                        'kwargs_count': len(kwargs),
                        'success': True
                    })
                
                return result
                
            except Exception as e:
                # Record error metrics
                execution_time = time.time() - start_time
                
                with self._lock:
                    metrics = self.metrics[func.__name__]
                    metrics['error_count'] += 1
                    metrics['call_history'].append({
                        'timestamp': datetime.now(),
                        'execution_time': execution_time,
                        'args_count': len(args),
                        'kwargs_count': len(kwargs),
                        'success': False,
                        'error': str(e)
                    })
                
                raise
        
        # Add analysis methods to the wrapped function
        wrapper.get_stats = lambda: self._get_stats(func.__name__)
        wrapper.get_detailed_report = lambda: self._get_detailed_report(func.__name__)
        wrapper.reset_stats = lambda: self._reset_stats(func.__name__)
        
        return wrapper
    
    def _get_stats(self, func_name):
        """Get basic statistics for a function"""
        with self._lock:
            metrics = self.metrics[func_name]
            return {
                'function_name': func_name,
                'call_count': metrics['call_count'],
                'total_time': metrics['total_time'],
                'average_time': metrics['avg_time'],
                'min_time': metrics['min_time'] if metrics['min_time'] != float('inf') else 0,
                'max_time': metrics['max_time'],
                'error_count': metrics['error_count'],
                'success_rate': ((metrics['call_count'] - metrics['error_count']) / 
                               max(metrics['call_count'], 1)) * 100,
                'last_called': metrics['last_called']
            }
    
    def _get_detailed_report(self, func_name):
        """Get detailed performance report"""
        with self._lock:
            metrics = self.metrics[func_name]
            
            # Calculate memory statistics
            memory_stats = None
            if self.track_memory and metrics['memory_usage']:
                memory_deltas = [m['delta'] for m in metrics['memory_usage']]
                memory_stats = {
                    'avg_memory_change': sum(memory_deltas) / len(memory_deltas),
                    'max_memory_increase': max(memory_deltas),
                    'min_memory_change': min(memory_deltas)
                }
            
            # Calculate recent performance trend
            recent_calls = list(metrics['call_history'])[-10:]  # Last 10 calls
            if len(recent_calls) > 1:
                recent_times = [c['execution_time'] for c in recent_calls if c['success']]
                trend = "improving" if len(recent_times) > 1 and recent_times[-1] < recent_times[0] else "stable"
            else:
                trend = "insufficient_data"
            
            return {
                **self._get_stats(func_name),
                'memory_stats': memory_stats,
                'performance_trend': trend,
                'recent_calls': recent_calls
            }
    
    def _reset_stats(self, func_name):
        """Reset statistics for a function"""
        with self._lock:
            if func_name in self.metrics:
                del self.metrics[func_name]
    
    def get_global_stats(self):
        """Get statistics for all monitored functions"""
        with self._lock:
            return {name: self._get_stats(name) for name in self.metrics.keys()}

# Create performance monitor instance
monitor = PerformanceMonitor(track_memory=True, track_cpu=True)

@monitor
def cpu_intensive_task(iterations=1000000):
    """Simulate CPU-intensive computation"""
    total = 0
    for i in range(iterations):
        total += i ** 2
    return total

@monitor  
def memory_intensive_task(size=1000000):
    """Simulate memory-intensive task"""
    # Create large list
    data = list(range(size))
    # Process data
    result = sum(x * 2 for x in data if x % 2 == 0)
    return result

@monitor
def io_simulation(delay=0.1):
    """Simulate I/O operation"""
    time.sleep(delay)
    return f"I/O operation completed in {delay}s"

@monitor
def unreliable_function():
    """Function that sometimes fails"""
    import random
    if random.random() < 0.3:  # 30% failure rate
        raise Exception("Random failure occurred")
    time.sleep(0.05)
    return "Success"

# Demo performance monitoring
def demo_performance_monitoring():
    print("📊 Performance Monitoring Demo\n")
    
    # Run various functions multiple times
    print("🔄 Running CPU intensive tasks...")
    for i in range(3):
        cpu_intensive_task(500000)
    
    print("🔄 Running memory intensive tasks...")
    for i in range(3):
        memory_intensive_task(500000)
    
    print("🔄 Running I/O simulations...")
    for i in range(5):
        io_simulation(0.02)
    
    print("🔄 Running unreliable function...")
    for i in range(10):
        try:
            unreliable_function()
        except Exception:
            pass  # Expected failures
    
    # Display performance reports
    print("\n📈 Performance Reports:")
    print("=" * 60)
    
    for func in [cpu_intensive_task, memory_intensive_task, io_simulation, unreliable_function]:
        stats = func.get_stats()
        print(f"\n🎯 {stats['function_name']}:")
        print(f"   📞 Calls: {stats['call_count']}")
        print(f"   ⏱️ Avg Time: {stats['average_time']:.4f}s")
        print(f"   ⏱️ Min/Max: {stats['min_time']:.4f}s / {stats['max_time']:.4f}s")
        print(f"   ✅ Success Rate: {stats['success_rate']:.1f}%")
        
        if stats['error_count'] > 0:
            print(f"   ❌ Errors: {stats['error_count']}")
    
    # Show global statistics
    print(f"\n🌐 Global Statistics:")
    global_stats = monitor.get_global_stats()
    total_calls = sum(stat['call_count'] for stat in global_stats.values())
    total_time = sum(stat['total_time'] for stat in global_stats.values())
    print(f"   📊 Total function calls: {total_calls}")
    print(f"   ⏱️ Total execution time: {total_time:.4f}s")

demo_performance_monitoring()
```

### 🔄 Caching & Memoization Strategies

```python
import time
import pickle
import hashlib
import threading
from functools import wraps
from datetime import datetime, timedelta
from typing import Any, Optional, Callable

class SmartCache:
    """
    Advanced caching system with multiple strategies
    """
    
    def __init__(self, 
                 max_size: int = 128,
                 ttl: Optional[int] = None,
                 strategy: str = "lru",  # lru, lfu, fifo
                 persistent: bool = False,
                 cache_file: str = "cache.pkl"):
        
        self.max_size = max_size
        self.ttl = ttl
        self.strategy = strategy
        self.persistent = persistent
        self.cache_file = cache_file
        
        self._cache = {}
        self._access_times = {}  # For LRU
        self._access_counts = {}  # For LFU
        self._insertion_order = []  # For FIFO
        self._expiry_times = {}  # For TTL
        self._lock = threading.RLock()
        
        if persistent:
            self._load_cache()
    
    def _create_key(self, func: Callable, args: tuple, kwargs: dict) -> str:
        """Create a unique cache key"""
        key_data = {
            'func_name': func.__name__,
            'func_module': func.__module__,
            'args': args,
            'kwargs': sorted(kwargs.items())
        }
        key_str = str(key_data)
        return hashlib.md5(key_str.encode()).hexdigest()
    
    def _is_expired(self, key: str) -> bool:
        """Check if cache entry has expired"""
        if self.ttl and key in self._expiry_times:
            return datetime.now() > self._expiry_times[key]
        return False
    
    def _evict_expired(self):
        """Remove expired entries"""
        if not self.ttl:
            return
            
        current_time = datetime.now()
        expired_keys = [
            key for key, expiry in self._expiry_times.items()
            if current_time > expiry
        ]
        
        for key in expired_keys:
            self._remove_key(key)
    
    def _remove_key(self, key: str):
        """Remove a key and all its metadata"""
        self._cache.pop(key, None)
        self._access_times.pop(key, None)
        self._access_counts.pop(key, None)
        self._expiry_times.pop(key, None)
        if key in self._insertion_order:
            self._insertion_order.remove(key)
    
    def _evict_by_strategy(self):
        """Evict entries based on the chosen strategy"""
        if len(self._cache) < self.max_size:
            return
        
        if self.strategy == "lru":
            # Remove least recently used
            if self._access_times:
                oldest_key = min(self._access_times, key=self._access_times.get)
                self._remove_key(oldest_key)
        
        elif self.strategy == "lfu":
            # Remove least frequently used
            if self._access_counts:
                least_used_key = min(self._access_counts, key=self._access_counts.get)
                self._remove_key(least_used_key)
        
        elif self.strategy == "fifo":
            # Remove first inserted
            if self._insertion_order:
                oldest_key = self._insertion_order.pop(0)
                self._remove_key(oldest_key)
    
    def _load_cache(self):
        """Load cache from persistent storage"""
        try:
            with open(self.cache_file, 'rb') as f:
                data = pickle.load(f)
                self._cache = data.get('cache', {})
                self._access_times = data.get('access_times', {})
                self._access_counts = data.get('access_counts', {})
                self._insertion_order = data.get('insertion_order', [])
                self._expiry_times = data.get('expiry_times', {})
            print(f"💾 Loaded {len(self._cache)} cached items from {self.cache_file}")
        except (FileNotFoundError, pickle.PickleError):
            print(f"📝 Starting with empty cache (no existing {self.cache_file})")
    
    def _save_cache(self):
        """Save cache to persistent storage"""
        if not self.persistent:
            return
            
        try:
            data = {
                'cache': self._cache,
                'access_times': self._access_times,
                'access_counts': self._access_counts,
                'insertion_order': self._insertion_order,
                'expiry_times': self._expiry_times
            }
            with open(self.cache_file, 'wb') as f:
                pickle.dump(data, f)
        except Exception as e:
            print(f"⚠️ Failed to save cache: {e}")
    
    def __call__(self, func: Callable):
        @wraps(func)
        def wrapper(*args, **kwargs):
            with self._lock:
                # Create cache key
                key = self._create_key(func, args, kwargs)
                
                # Clean expired entries
                self._evict_expired()
                
                # Check if result is cached and not expired
                if key in self._cache and not self._is_expired(key):
                    # Update access metadata
                    self._access_times[key] = time.time()
                    self._access_counts[key] = self._access_counts.get(key, 0) + 1
                    
                    print(f"💾 Cache HIT for {func.__name__} (strategy: {self.strategy})")
                    return self._cache[key]
                
                # Compute result
                print(f"🔄 Computing {func.__name__} (cache miss)")
                start_time = time.time()
                result = func(*args, **kwargs)
                compute_time = time.time() - start_time
                
                # Store in cache
                self._evict_by_strategy()  # Make room if needed
                
                self._cache[key] = result
                self._access_times[key] = time.time()
                self._access_counts[key] = 1
                self._insertion_order.append(key)
                
                # Set expiry if TTL is configured
                if self.ttl:
                    self._expiry_times[key] = datetime.now() + timedelta(seconds=self.ttl)
                
                # Save to persistent storage if configured
                self._save_cache()
                
                print(f"💾 Cached result for {func.__name__} (computed in {compute_time:.4f}s)")
                return result
        
        # Add cache management methods
        wrapper.cache_info = self.get_cache_info
        wrapper.cache_clear = self.clear_cache
        wrapper.cache_stats = self.get_detailed_stats
        
        return wrapper
    
    def get_cache_info(self) -> dict:
        """Get basic cache information"""
        with self._lock:
            return {
                'size': len(self._cache),
                'max_size': self.max_size,
                'strategy': self.strategy,
                'ttl': self.ttl,
                'hit_rate': self._calculate_hit_rate()
            }
    
    def get_detailed_stats(self) -> dict:
        """Get detailed cache statistics"""
        with self._lock:
            current_time = time.time()
            
            # Calculate access statistics
            if self._access_times:
                oldest_access = min(self._access_times.values())
                newest_access = max(self._access_times.values())
                avg_age = current_time - (sum(self._access_times.values()) / len(self._access_times))
            else:
                oldest_access = newest_access = avg_age = 0
            
            return {
                **self.get_cache_info(),
                'oldest_access_age': current_time - oldest_access if oldest_access else 0,
                'newest_access_age': current_time - newest_access if newest_access else 0,
                'average_entry_age': avg_age,
                'total_access_count': sum(self._access_counts.values()),
                'most_accessed_count': max(self._access_counts.values()) if self._access_counts else 0
            }
    
    def _calculate_hit_rate(self) -> float:
        """Calculate cache hit rate (simplified)"""
        # This is a simplified calculation - in a real implementation,
        # you'd track hits and misses separately
        total_accesses = sum(self._access_counts.values())
        return (total_accesses - len(self._cache)) / max(total_accesses, 1) * 100
    
    def clear_cache(self):
        """Clear all cached data"""
        with self._lock:
            self._cache.clear()
            self._access_times.clear()
            self._access_counts.clear()
            self._insertion_order.clear()
            self._expiry_times.clear()
            
            if self.persistent:
                self._save_cache()

# Create different cache configurations
lru_cache = SmartCache(max_size=5, strategy="lru", persistent=False)
lfu_cache = SmartCache(max_size=3, strategy="lfu", persistent=False)
ttl_cache = SmartCache(max_size=10, ttl=5, strategy="lru", persistent=False)  # 5 second TTL

@lru_cache
def fibonacci_lru(n):
    """Fibonacci with LRU caching"""
    if n < 2:
        return n
    return fibonacci_lru(n-1) + fibonacci_lru(n-2)

@lfu_cache  
def expensive_computation(n, multiplier=1):
    """Expensive computation with LFU caching"""
    time.sleep(0.1)  # Simulate expensive work
    return (n ** 2 + n) * multiplier

@ttl_cache
def time_sensitive_data(query):
    """Time-sensitive data with TTL caching"""
    time.sleep(0.05)  # Simulate API call
    return f"Data for '{query}' at {datetime.now().strftime('%H:%M:%S')}"

# Demo caching strategies
def demo_caching_strategies():
    print("💾 Advanced Caching Strategies Demo\n")
    
    # Test LRU cache with Fibonacci
    print("🔄 Testing LRU Cache (Fibonacci):")
    for i in [10, 5, 10, 8, 10]:  # 10 should be cached, evicted, then recomputed
        result = fibonacci_lru(i)
        print(f"   fib({i}) = {result}")
    
    print(f"   📊 LRU Cache stats: {fibonacci_lru.cache_info()}")
    
    print("\n🔄 Testing LFU Cache (Expensive Computation):")
    # Test LFU cache - frequently accessed items should stay
    queries = [
        (5, 1), (10, 1), (5, 1), (15, 1),  # 5 accessed twice, should stay
        (20, 1), (5, 1), (25, 1)  # 5 accessed again, others might be evicted
    ]
    
    for n, mult in queries:
        result = expensive_computation(n, mult)
        print(f"   compute({n}, {mult}) = {result}")
    
    print(f"   📊 LFU Cache stats: {expensive_computation.cache_info()}")
    
    print("\n⏰ Testing TTL Cache (Time-Sensitive Data):")
    # Test TTL cache - data should expire after 5 seconds
    queries = ["weather", "news", "weather"]
    
    for query in queries:
        result = time_sensitive_data(query)
        print(f"   query('{query}') = {result}")
        if query == "news":
            print("   ⏳ Waiting 6 seconds for TTL expiration...")
            time.sleep(6)
    
    print(f"   📊 TTL Cache stats: {time_sensitive_data.cache_stats()}")
    
    # Final query to show data was refreshed
    result = time_sensitive_data("weather")
    print(f"   query('weather') after TTL = {result}")

demo_caching_strategies()
```

---

## 🎯 Best Practices & Performance

### ⚡ Performance Considerations

```python
import time
import functools
from memory_profiler import profile
from functools import wraps

def performance_comparison():
    """
    Compare performance impact of different decorator approaches
    """
    
    # Baseline function - no decoration
    def baseline_function(x, y):
        return x + y
    
    # Simple decorator with minimal overhead
    def minimal_decorator(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            return func(*args, **kwargs)
        return wrapper
    
    # Heavy decorator with logging and validation
    def heavy_decorator(func):
        @wraps(func)  
        def wrapper(*args, **kwargs):
            # Heavy logging
            import logging
            logging.basicConfig(level=logging.INFO)
            logger = logging.getLogger(__name__)
            
            # Input validation
            for arg in args:
                if not isinstance(arg, (int, float)):
                    raise TypeError(f"Expected number, got {type(arg)}")
            
            # Pre-execution logging
            logger.info(f"Executing {func.__name__} with args: {args}")
            
            # Timing
            start = time.time()
            result = func(*args, **kwargs)
            duration = time.time() - start
            
            # Post-execution logging
            logger.info(f"Completed {func.__name__} in {duration:.6f}s")
            
            return result
        return wrapper
    
    # Optimized decorator - minimal overhead but useful features
    def optimized_decorator(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            # Only time if in debug mode
            if __debug__:
                start = time.perf_counter()
                result = func(*args, **kwargs)
                # Only log if execution takes > 1ms
                duration = time.perf_counter() - start
                if duration > 0.001:
                    print(f"⚠️ Slow execution: {func.__name__} took {duration:.4f}s")
                return result
            else:
                return func(*args, **kwargs)
        return wrapper
    
    # Apply decorators
    @minimal_decorator
    def minimal_function(x, y):
        return x + y
    
    @heavy_decorator
    def heavy_function(x, y):
        return x + y
    
    @optimized_decorator  
    def optimized_function(x, y):
        return x + y
    
    # Benchmark functions
    def benchmark_function(func, name, iterations=100000):
        start = time.perf_counter()
        for i in range(iterations):
            func(i, i + 1)
        duration = time.perf_counter() - start
        
        overhead = (duration / iterations) * 1000000  # microseconds per call
        print(f"📊 {name:<20}: {duration:.4f}s total, {overhead:.2f}μs per call")
        return duration
    
    print("⚡ Performance Impact of Decorators")
    print("=" * 50)
    
    iterations = 100000
    
    baseline_time = benchmark_function(baseline_function, "Baseline", iterations)
    minimal_time = benchmark_function(minimal_function, "Minimal Decorator", iterations)
    optimized_time = benchmark_function(optimized_function, "Optimized Decorator", iterations)
    
    # Skip heavy decorator for large iterations (too slow)
    heavy_time = benchmark_function(heavy_function, "Heavy Decorator", 1000)
    heavy_time = heavy_time * (iterations / 1000)  # Extrapolate
    
    print(f"\n📈 Performance Analysis:")
    print(f"   Minimal overhead: {((minimal_time / baseline_time - 1) * 100):.1f}%")
    print(f"   Optimized overhead: {((optimized_time / baseline_time - 1) * 100):.1f}%")  
    print(f"   Heavy overhead (estimated): {((heavy_time / baseline_time - 1) * 100):.0f}%")

# Run performance comparison
performance_comparison()
```

### 🎯 Best Practices Guide

```python
# ✅ GOOD: Use functools.wraps to preserve function metadata
from functools import wraps

def good_decorator(func):
    @wraps(func)  # Preserves __name__, __doc__, etc.
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        return func(*args, **kwargs)
    return wrapper

# ❌ BAD: No wraps - loses function metadata
def bad_decorator(func):
    def wrapper(*args, **kwargs):
        print(f"Calling function")  # Can't access func.__name__ properly
        return func(*args, **kwargs)
    return wrapper

# ✅ GOOD: Handle both args and kwargs properly
def flexible_decorator(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        # Can handle any function signature
        return func(*args, **kwargs)
    return wrapper

# ❌ BAD: Fixed signature - won't work with all functions
def inflexible_decorator(func):
    @wraps(func)
    def wrapper(arg1, arg2):  # Only works with 2-arg functions
        return func(arg1, arg2)
    return wrapper

# ✅ GOOD: Parameterized decorator with proper factory pattern
def configurable_decorator(enable_feature=True, log_level="INFO"):
    def decorator(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            if enable_feature:
                print(f"[{log_level}] Executing {func.__name__}")
            return func(*args, **kwargs)
        return wrapper
    return decorator

# ❌ BAD: Global state in decorator
_global_state = {}

def stateful_decorator(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        # Using global state - not thread-safe, hard to test
        _global_state[func.__name__] = time.time()
        return func(*args, **kwargs)
    return wrapper

# ✅ GOOD: Thread-safe decorator with local state
import threading

def thread_safe_decorator(func):
    call_count = threading.local()
    
    @wraps(func)
    def wrapper(*args, **kwargs):
        if not hasattr(call_count, 'value'):
            call_count.value = 0
        call_count.value += 1
        
        print(f"Thread-local call #{call_count.value} to {func.__name__}")
        return func(*args, **kwargs)
    return wrapper

# ✅ GOOD: Decorator with proper error handling
def safe_decorator(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        try:
            result = func(*args, **kwargs)
            print(f"✅ {func.__name__} completed successfully")
            return result
        except Exception as e:
            print(f"❌ {func.__name__} failed: {e}")
            # Re-raise to maintain original exception behavior
            raise
    return wrapper

# ✅ GOOD: Conditional decorator for debug/production
def debug_only(func):
    """Decorator that only applies in debug mode"""
    if __debug__:
        @wraps(func)
        def wrapper(*args, **kwargs):
            print(f"🐛 DEBUG: Calling {func.__name__}")
            result = func(*args, **kwargs)
            print(f"🐛 DEBUG: {func.__name__} returned {result}")
            return result
        return wrapper
    else:
        # In production, return function unchanged (zero overhead)
        return func

# ✅ GOOD: Memory-efficient decorator for caching
def efficient_cache(maxsize=128):
    def decorator(func):
        cache = {}
        
        @wraps(func)
        def wrapper(*args, **kwargs):
            # Create efficient cache key
            key = hash((args, tuple(sorted(kwargs.items()))))
            
            if key in cache:
                return cache[key]
            
            result = func(*args, **kwargs)
            
            # Manage cache size efficiently
            if len(cache) >= maxsize:
                # Remove oldest entry (simple FIFO)
                oldest_key = next(iter(cache))
                del cache[oldest_key]
            
            cache[key] = result
            return result
        
        wrapper.cache_clear = cache.clear
        wrapper.cache_info = lambda: {"size": len(cache), "maxsize": maxsize}
        return wrapper
    return decorator

# Performance-Conscious Decorator Design Guidelines
class DecoratorGuidelines:
    """
    📋 Decorator Best Practices Checklist:
    
    ✅ ALWAYS:
    - Use @functools.wraps(func) to preserve metadata
    - Handle *args and **kwargs for flexibility
    - Re-raise exceptions to maintain original behavior
    - Consider thread-safety for stateful decorators
    - Document decorator behavior clearly
    - Provide cache_clear() and cache_info() for caching decorators
    
    ⚡ PERFORMANCE:
    - Minimize work in the wrapper function
    - Use conditional logic to skip expensive operations
    - Consider __debug__ flag for development-only features
    - Profile decorator overhead in performance-critical code
    - Use efficient data structures for state management
    
    🏗️ ARCHITECTURE:
    - Keep decorators focused on a single responsibility
    - Make decorators composable and order-independent when possible
    - Provide configuration options through parameters
    - Avoid global state and side effects
    - Design for testability
    
    🔒 THREAD SAFETY:
    - Use threading.local() for per-thread state
    - Use locks for shared mutable state
    - Prefer immutable data structures when possible
    - Be careful with closure variables in multi-threaded environments
    
    🧪 TESTING:
    - Test decorated and undecorated function behavior
    - Test decorator configuration options
    - Test error handling and edge cases
    - Verify metadata preservation
    - Test thread safety if applicable
    """
    pass

# Example of production-ready decorator following all guidelines
def production_monitor(
    enable_timing: bool = True,
    enable_logging: bool = True,
    cache_results: bool = False,
    cache_size: int = 128
):
    """
    Production-ready monitoring decorator with comprehensive features
    
    Args:
        enable_timing: Whether to measure execution time
        enable_logging: Whether to log function calls
        cache_results: Whether to cache function results
        cache_size: Maximum cache size if caching is enabled
    """
    def decorator(func):
        # Initialize decorator state
        cache = {} if cache_results else None
        stats = {'calls': 0, 'total_time': 0, 'errors': 0}
        lock = threading.Lock()
        
        @wraps(func)
        def wrapper(*args, **kwargs):
            with lock:
                stats['calls'] += 1
            
            # Check cache first if enabled
            if cache_results:
                try:
                    key = hash((args, tuple(sorted(kwargs.items()))))
                    if key in cache:
                        return cache[key]
                except TypeError:
                    # Args not hashable, skip caching for this call
                    pass
            
            # Timing and logging
            start_time = time.perf_counter() if enable_timing else None
            
            if enable_logging and __debug__:
                print(f"📞 Calling {func.__name__}")
            
            try:
                result = func(*args, **kwargs)
                
                # Update timing stats
                if enable_timing:
                    duration = time.perf_counter() - start_time
                    with lock:
                        stats['total_time'] += duration
                
                # Cache result if enabled
                if cache_results and 'key' in locals():
                    if len(cache) >= cache_size:
                        # Remove oldest entry
                        oldest_key = next(iter(cache))
                        del cache[oldest_key]
                    cache[key] = result
                
                return result
                
            except Exception as e:
                with lock:
                    stats['errors'] += 1
                
                if enable_logging:
                    print(f"❌ {func.__name__} failed: {e}")
                
                raise
        
        # Add utility methods
        def get_stats():
            with lock:
                avg_time = stats['total_time'] / max(stats['calls'], 1)
                return {
                    'calls': stats['calls'],
                    'total_time': stats['total_time'],
                    'average_time': avg_time,
                    'errors': stats['errors'],
                    'success_rate': (stats['calls'] - stats['errors']) / max(stats['calls'], 1)
                }
        
        wrapper.get_stats = get_stats
        if cache_results:
            wrapper.cache_clear = lambda: cache.clear()
            wrapper.cache_info = lambda: {'size': len(cache), 'maxsize': cache_size}
        
        return wrapper
    return decorator

# Demo production decorator
@production_monitor(
    enable_timing=True,
    enable_logging=True,
    cache_results=True,
    cache_size=10
)
def example_function(x, y):
    """Example function using production decorator"""
    time.sleep(0.001)  # Simulate some work
    return x * y + x + y

# Test the production decorator
for i in range(5):
    result = example_function(i, i+1)
    if i == 2:
        result = example_function(0, 1)  # Should hit cache

print(f"📊 Function stats: {example_function.get_stats()}")
if hasattr(example_function, 'cache_info'):
    print(f"💾 Cache info: {example_function.cache_info()}")
```

---

## 🧪 Interactive Exercises

### 🎮 Exercise 1: Build Your Own Retry Decorator

```python
"""
🎯 CHALLENGE: Create a Smart Retry Decorator

Requirements:
1. Retry failed functions with exponential backoff
2. Allow custom exceptions to trigger retries
3. Log retry attempts
4. Provide detailed statistics
5. Support async functions

Your implementation should handle:
- Maximum retry attempts
- Exponential backoff with jitter
- Specific exception types to retry on
- Comprehensive logging
"""

import asyncio
import random
import time
from functools import wraps
from typing import Type, Tuple, Union, Callable

def smart_retry(
    max_attempts: int = 3,
    base_delay: float = 1.0,
    max_delay: float = 60.0,
    exponential_base: float = 2.0,
    jitter: bool = True,
    retry_exceptions: Tuple[Type[Exception], ...] = (Exception,)
):
    """
    Smart retry decorator with exponential backoff and jitter
    
    TODO: Implement this decorator following the requirements above
    """
    # YOUR CODE HERE
    pass

# Test your decorator with these functions:

@smart_retry(max_attempts=3, retry_exceptions=(ValueError, RuntimeError))
def flaky_function(success_rate: float = 0.3):
    """Function that fails randomly"""
    if random.random() > success_rate:
        raise ValueError("Random failure occurred")
    return "Success!"

@smart_retry(max_attempts=4, base_delay=0.5, max_delay=5.0)
async def flaky_async_function(success_rate: float = 0.4):
    """Async function that fails randomly"""
    await asyncio.sleep(0.1)
    if random.random() > success_rate:
        raise RuntimeError("Async failure occurred")
    return "Async success!"

# Test your implementation:
# result = flaky_function(0.7)
# async_result = asyncio.run(flaky_async_function(0.6))
```

### 🎮 Exercise 2: Create a Rate Limiting Decorator

```python
"""
🎯 CHALLENGE: Build an Advanced Rate Limiter

Requirements:
1. Implement token bucket algorithm
2. Support different rate limits per user/key
3. Provide burst capacity
4. Thread-safe implementation
5. Detailed rate limit status

Your rate limiter should:
- Allow X requests per Y seconds
- Handle burst traffic up to a limit
- Track separate limits for different keys
- Provide informative error messages
"""

import threading
import time
from collections import defaultdict
from functools import wraps

class TokenBucket:
    """
    TODO: Implement token bucket algorithm
    
    Should support:
    - tokens_per_second: Rate at which tokens are added
    - bucket_capacity: Maximum tokens that can be stored
    - Thread-safe token consumption
    """
    # YOUR CODE HERE
    pass

def rate_limit(
    requests_per_second: float = 1.0,
    burst_capacity: int = 5,
    key_func: Callable = None  # Function to extract rate limit key
):
    """
    TODO: Implement rate limiting decorator
    
    Should use TokenBucket to enforce limits per key
    """
    # YOUR CODE HERE
    pass

# Test functions for your rate limiter:

@rate_limit(requests_per_second=2.0, burst_capacity=3)
def api_endpoint(data):
    """Simulated API endpoint"""
    return f"Processed: {data}"

@rate_limit(
    requests_per_second=1.0,
    burst_capacity=2,
    key_func=lambda user_id, *args, **kwargs: f"user_{user_id}"
)
def user_specific_endpoint(user_id, action):
    """API endpoint with per-user rate limiting"""
    return f"User {user_id} performed {action}"

# Test your rate limiter:
# for i in range(10):
#     try:
#         result = api_endpoint(f"data_{i}")
#         print(f"✅ {result}")
#     except Exception as e:
#         print(f"❌ {e}")
#     time.sleep(0.3)
```

### 🎮 Exercise 3: Build a Circuit Breaker Decorator

```python
"""
🎯 CHALLENGE: Implement Circuit Breaker Pattern

Requirements:
1. Three states: CLOSED, OPEN, HALF_OPEN
2. Configurable failure threshold
3. Automatic recovery attempts
4. Detailed state reporting
5. Support for custom failure detection

Circuit Breaker States:
- CLOSED: Normal operation, failures are counted
- OPEN: Failures exceeded threshold, all calls fail fast
- HALF_OPEN: Testing if service has recovered
"""

from enum import Enum
import time
from functools import wraps
from typing import Callable, Type, Tuple

class CircuitBreakerState(Enum):
    CLOSED = "CLOSED"
    OPEN = "OPEN"
    HALF_OPEN = "HALF_OPEN"

class CircuitBreakerOpenError(Exception):
    """Raised when circuit breaker is in OPEN state"""
    pass

def circuit_breaker(
    failure_threshold: int = 5,
    recovery_timeout: float = 60.0,
    expected_exception: Tuple[Type[Exception], ...] = (Exception,),
    success_threshold: int = 3  # Successes needed in HALF_OPEN to close
):
    """
    TODO: Implement circuit breaker decorator
    
    Track:
    - Current state
    - Failure count
    - Last failure time
    - Success count (in HALF_OPEN state)
    
    Behavior:
    - CLOSED -> OPEN when failure_threshold reached
    - OPEN -> HALF_OPEN after recovery_timeout
    - HALF_OPEN -> CLOSED after success_threshold successes
    - HALF_OPEN -> OPEN on any failure
    """
    # YOUR CODE HERE
    pass

# Test your circuit breaker:

@circuit_breaker(failure_threshold=3, recovery_timeout=5.0)
def unreliable_service(failure_rate: float = 0.7):
    """Service that fails randomly"""
    if random.random() < failure_rate:
        raise ConnectionError("Service unavailable")
    return "Service response"

# Test circuit breaker behavior:
# for i in range(20):
#     try:
#         result = unreliable_service(0.8)  # High failure rate
#         print(f"✅ Call {i}: {result}")
#     except Exception as e:
#         print(f"❌ Call {i}: {e}")
#     
#     time.sleep(1)
#     
#     # Check circuit breaker state
#     if hasattr(unreliable_service, 'get_state'):
#         state = unreliable_service.get_state()
#         print(f"   Circuit state: {state}")
```

### 🎯 Solutions & Explanations

<details>
<summary>💡 Click to see Exercise 1 Solution</summary>

```python
def smart_retry(
    max_attempts: int = 3,
    base_delay: float = 1.0,
    max_delay: float = 60.0,
    exponential_base: float = 2.0,
    jitter: bool = True,
    retry_exceptions: Tuple[Type[Exception], ...] = (Exception,)
):
    def decorator(func):
        retry_stats = {'total_attempts': 0, 'total_retries': 0, 'failures': 0}
        
        if asyncio.iscoroutinefunction(func):
            @wraps(func)
            async def async_wrapper(*args, **kwargs):
                last_exception = None
                
                for attempt in range(max_attempts):
                    retry_stats['total_attempts'] += 1
                    
                    try:
                        result = await func(*args, **kwargs)
                        if attempt > 0:
                            print(f"✅ {func.__name__} succeeded on attempt {attempt + 1}")
                        return result
                    
                    except retry_exceptions as e:
                        last_exception = e
                        retry_stats['total_retries'] += 1
                        
                        if attempt < max_attempts - 1:  # Don't delay after last attempt
                            delay = min(base_delay * (exponential_base ** attempt), max_delay)
                            if jitter:
                                delay *= (0.5 + random.random())  # Add ±50% jitter
                            
                            print(f"⚠️ Attempt {attempt + 1} failed: {e}")
                            print(f"🔄 Retrying in {delay:.2f}s...")
                            await asyncio.sleep(delay)
                    
                    except Exception as e:
                        # Don't retry for exceptions not in retry_exceptions
                        print(f"❌ Non-retryable error: {e}")
                        raise
                
                retry_stats['failures'] += 1
                print(f"💀 All {max_attempts} attempts failed")
                raise last_exception
            
            async_wrapper.get_stats = lambda: retry_stats
            return async_wrapper
        
        else:
            @wraps(func)
            def sync_wrapper(*args, **kwargs):
                last_exception = None
                
                for attempt in range(max_attempts):
                    retry_stats['total_attempts'] += 1
                    
                    try:
                        result = func(*args, **kwargs)
                        if attempt > 0:
                            print(f"✅ {func.__name__} succeeded on attempt {attempt + 1}")
                        return result
                    
                    except retry_exceptions as e:
                        last_exception = e
                        retry_stats['total_retries'] += 1
                        
                        if attempt < max_attempts - 1:
                            delay = min(base_delay * (exponential_base ** attempt), max_delay)
                            if jitter:
                                delay *= (0.5 + random.random())
                            
                            print(f"⚠️ Attempt {attempt + 1} failed: {e}")
                            print(f"🔄 Retrying in {delay:.2f}s...")
                            time.sleep(delay)
                    
                    except Exception as e:
                        print(f"❌ Non-retryable error: {e}")
                        raise
                
                retry_stats['failures'] += 1
                print(f"💀 All {max_attempts} attempts failed")
                raise last_exception
            
            sync_wrapper.get_stats = lambda: retry_stats
            return sync_wrapper
    
    return decorator
```

</details>

---

## 🎉 Conclusion

Congratulations! You've mastered the art of Python decorators! 🎭

### 🌟 What You've Learned:

- **🧠 Core Concepts**: Functions as first-class objects, closure mechanics
- **🔧 Basic Patterns**: Simple decorators, argument handling, metadata preservation  
- **⚡ Advanced Techniques**: Parameterized decorators, class-based decorators, async support
- **🏗️ Built-in Decorators**: @property, @staticmethod, @classmethod, @functools.lru_cache
- **🔗 Composition**: Chaining multiple decorators effectively
- **💼 Real-World Applications**: Authentication, performance monitoring, caching
- **🎯 Best Practices**: Performance optimization, thread safety, testing strategies

### 🚀 Next Steps:

1. **Practice Building**: Create decorators for your own projects
2. **Explore Libraries**: Study decorator usage in Flask, Django, FastAPI
3. **Performance Tuning**: Profile decorator overhead in your applications
4. **Advanced Patterns**: Investigate metaclasses and descriptor protocols
5. **Contribute**: Build reusable decorator libraries for the community

### 💎 Key Takeaways:

```
🎯 Decorators are powerful but use them wisely
⚡ Performance matters - profile your decorators  
🔒 Thread safety is crucial for stateful decorators
🧪 Test both decorated and undecorated behavior
📚 Always use @functools.wraps to preserve metadata
```

Remember: **Great power comes with great responsibility!** Use decorators to make your code more elegant, maintainable, and powerful. 

Happy decorating! 🎉✨

---

### 📖 Additional Resources

- **📚 Official Documentation**: [Python Decorators](https://docs.python.org/3/glossary.html#term-decorator)
- **🎓 Real Python**: [Primer on Python Decorators](https://realpython.com/primer-on-python-decorators/)
- **📖 PEP 318**: [Decorators for Functions and Methods](https://www.python.org/dev/peps/pep-0318/)
- **🏗️ Design Patterns**: [Decorator Pattern](https://refactoring.guru/design-patterns/decorator)
- **⚡ Performance**: [Python Performance Tips](https://wiki.python.org/moin/PythonSpeed/PerformanceTips)

---

*Made with ❤️ for Python developers who want to master decorators and write more elegant, maintainable code.*