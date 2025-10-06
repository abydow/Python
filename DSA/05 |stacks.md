# 🐍 Python Stacks: The Complete Interactive Guide
*Master the Art of Stack Data Structure in Python*

[![Python Stacks](https://img.shields.io/badge/Python-Stacks-blue?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
![Topic](https://img.shields.io/badge/Topic-Data%20Structures-green?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-Beginner%20to%20Advanced-orange?style=for-the-badge)

---

## 🌟 Table of Contents
- [🔍 What is a Stack?](#-what-is-a-stack)
- [🏗️ LIFO Principle Visualization](#️-lifo-principle-visualization)
- [⚡ Core Stack Operations](#-core-stack-operations)
- [🎯 Implementation Methods](#-implementation-methods)
- [🚀 Performance Comparison](#-performance-comparison)
- [💡 Real-World Applications](#-real-world-applications)
- [🧪 Interactive Examples](#-interactive-examples)
- [📊 Best Practices](#-best-practices)

---

## 🔍 What is a Stack?

A **stack** is a linear data structure that follows the **Last-In/First-Out (LIFO)** principle. Think of it like a stack of books - you can only add or remove books from the top!

```
📚 Stack of Books Analogy:
    
    [   Book 3   ] ← Top (Last In, First Out)
    [   Book 2   ]
    [   Book 1   ] ← Bottom (First In, Last Out)
    ═════════════
```

### 🎭 Key Characteristics:
- **LIFO Ordering**: Last element added is the first to be removed
- **Single-Ended**: Operations only at one end (top)
- **Dynamic Size**: Can grow and shrink during runtime
- **Memory Efficient**: No gaps between elements

---

## 🏗️ LIFO Principle Visualization

### 📈 Stack Growth (Push Operations)
```
Step 1: Empty Stack           Step 2: Push 'A'              Step 3: Push 'B'
┌─────────────┐              ┌─────────────┐               ┌─────────────┐
│             │              │      A      │ ← top         │      B      │ ← top
│             │              │             │               │      A      │
│             │              │             │               │             │
│             │              │             │               │             │
└─────────────┘              └─────────────┘               └─────────────┘

Step 4: Push 'C'              Step 5: Push 'D'
┌─────────────┐              ┌─────────────┐
│      C      │ ← top        │      D      │ ← top
│      B      │              │      C      │
│      A      │              │      B      │
│             │              │      A      │
└─────────────┘              └─────────────┘
```

### 📉 Stack Shrinkage (Pop Operations)
```
Initial State                After Pop()                   After Pop()
┌─────────────┐              ┌─────────────┐               ┌─────────────┐
│      D      │ ← pop        │      C      │ ← top         │      B      │ ← top
│      C      │ ← top        │      B      │               │      A      │
│      B      │              │      A      │               │             │
│      A      │              │             │               │             │
└─────────────┘              └─────────────┘               └─────────────┘
    Returns 'D'                 Returns 'C'                    Returns 'B'
```

---

## ⚡ Core Stack Operations

### 🔄 Essential Operations Overview

```
┌─────────────────────────────────────────────────────────┐
│                  Stack Operations                       │
├─────────────────────────────────────────────────────────┤
│  Operation  │  Description            │  Time Complexity│
├─────────────┼─────────────────────────┼─────────────────┤
│   PUSH      │  Add element to top     │       O(1)      │
│   POP       │  Remove top element     │       O(1)      │
│   PEEK/TOP  │  View top element       │       O(1)      │
│   ISEMPTY   │  Check if stack empty   │       O(1)      │
│   SIZE      │  Get stack size         │       O(1)      │
└─────────────────────────────────────────────────────────┘
```

### 📝 Operation Details with ASCII

#### 1. 🔥 PUSH Operation
```python
def push(stack, element):
    """Add element to the top of the stack"""
    stack.append(element)
    print(f"Pushed '{element}' to stack")

# Visual Representation:
#    Before Push('X')          After Push('X')
#    ┌───────────┐            ┌───────────┐
#    │     C     │ ← top      │     X     │ ← top (NEW)
#    │     B     │            │     C     │
#    │     A     │            │     B     │
#    └───────────┘            │     A     │
#                             └───────────┘
```

#### 2. 💥 POP Operation
```python
def pop(stack):
    """Remove and return the top element"""
    if not stack:
        raise IndexError("Stack is empty!")
    return stack.pop()

# Visual Representation:
#    Before Pop()             After Pop()
#    ┌───────────┐            ┌───────────┐
#    │     Z     │ ← pop      │     Y     │ ← top
#    │     Y     │ ← top      │     X     │
#    │     X     │            │     W     │
#    │     W     │            └───────────┘
#    └───────────┘               Returns 'Z'
```

#### 3. 👁️ PEEK Operation
```python
def peek(stack):
    """View the top element without removing it"""
    if not stack:
        return None
    return stack[-1]

# Visual Representation:
#    ┌───────────┐
#    │     T     │ ← peek (returns 'T' without removing)
#    │     S     │
#    │     R     │   Stack remains unchanged
#    │     Q     │
#    └───────────┘
```

---

## 🎯 Implementation Methods

### 🎨 Method 1: Using Python List (Beginner-Friendly)

```python
class StackList:
    """Stack implementation using Python list"""
    
    def __init__(self):
        self.items = []
    
    def push(self, item):
        """Add item to top of stack"""
        self.items.append(item)
        self.visualize_stack()
    
    def pop(self):
        """Remove and return top item"""
        if self.is_empty():
            raise IndexError("🚨 Stack Underflow: Cannot pop from empty stack!")
        popped = self.items.pop()
        self.visualize_stack()
        return popped
    
    def peek(self):
        """Return top item without removing"""
        if self.is_empty():
            return None
        return self.items[-1]
    
    def is_empty(self):
        """Check if stack is empty"""
        return len(self.items) == 0
    
    def size(self):
        """Return number of items in stack"""
        return len(self.items)
    
    def visualize_stack(self):
        """ASCII visualization of current stack state"""
        print("\n📊 Current Stack State:")
        if self.is_empty():
            print("┌─────────────┐")
            print("│   EMPTY     │")
            print("└─────────────┘")
        else:
            print("┌─────────────┐")
            for i in range(len(self.items)-1, -1, -1):
                marker = "← top" if i == len(self.items)-1 else ""
                print(f"│  {str(self.items[i]):^9}  │ {marker}")
            print("└─────────────┘")
        print(f"Size: {self.size()}\n")

# 🧪 Interactive Example
stack = StackList()
print("🎮 Let's play with our stack!")

# Demonstrate push operations
for item in ['🍎', '🍌', '🍒']:
    print(f"Pushing {item}")
    stack.push(item)

# Demonstrate peek
print(f"👀 Peeking at top: {stack.peek()}")

# Demonstrate pop operations  
print(f"🎯 Popping: {stack.pop()}")
print(f"🎯 Popping: {stack.pop()}")
```

### 🚀 Method 2: Using collections.deque (Performance Optimized)

```python
from collections import deque

class StackDeque:
    """High-performance stack using deque"""
    
    def __init__(self):
        self.items = deque()
    
    def push(self, item):
        """O(1) push operation"""
        self.items.append(item)
    
    def pop(self):
        """O(1) pop operation"""
        if not self.items:
            raise IndexError("Stack underflow")
        return self.items.pop()
    
    def peek(self):
        """O(1) peek operation"""
        if not self.items:
            return None
        return self.items[-1]
    
    def is_empty(self):
        return len(self.items) == 0
    
    def __str__(self):
        return f"StackDeque({list(self.items)})"

# Performance Comparison Visualization:
"""
┌───────────────────────────────────────────┐
│             Performance Analysis          │
├────────────────┐────────────┐─────────────┤
│  Operation     │    List    │    Deque    │     
├────────────────┼────────────┼─────────────┤     
│  Push          │    O(1)*   │    O(1)     │     
│  Pop           │    O(1)    │    O(1)     │    
│  Peek          │    O(1)    │    O(1)     │     
│  Memory        │  Chunked   │  Consistent │     
└────────────────┘────────────┘─────────────┘
* List may need O(n) for reallocation
"""
```

### 🔒 Method 3: Thread-Safe Stack (queue.LifoQueue)

```python
from queue import LifoQueue

class ThreadSafeStack:
    """Thread-safe stack implementation"""
    
    def __init__(self, maxsize=0):
        self.stack = LifoQueue(maxsize)
    
    def push(self, item):
        """Thread-safe push"""
        self.stack.put(item)
    
    def pop(self, timeout=None):
        """Thread-safe pop with optional timeout"""
        try:
            return self.stack.get(timeout=timeout)
        except:
            raise IndexError("Stack is empty or timeout occurred")
    
    def peek(self):
        """Note: Peek is not atomic in LifoQueue"""
        if self.stack.empty():
            return None
        # This is not thread-safe, just for demonstration
        item = self.stack.get()
        self.stack.put(item)
        return item
    
    def is_empty(self):
        return self.stack.empty()
    
    def size(self):
        return self.stack.qsize()

# 🔐 Thread Safety Visualization:
"""
Thread 1: push(A) ──┐
                    ├─→ 🔒 LifoQueue 🔒 ──→ Safe Operations
Thread 2: pop()  ───┘
                    ↑
               Synchronized Access
"""
```

---

## 🚀 Performance Comparison

### 📊 Benchmark Results

```python
import time
from collections import deque

def benchmark_stacks():
    """Compare performance of different stack implementations"""
    
    n = 100000  # Number of operations
    
    print("🏁 Performance Benchmark Results")
    print("="*50)
    
    # Test List-based stack
    start = time.time()
    list_stack = []
    for i in range(n):
        list_stack.append(i)
    for i in range(n):
        list_stack.pop()
    list_time = time.time() - start
    
    # Test Deque-based stack
    start = time.time()
    deque_stack = deque()
    for i in range(n):
        deque_stack.append(i)
    for i in range(n):
        deque_stack.pop()
    deque_time = time.time() - start
    
    # Results visualization
    print(f"""
┌─────────────────────────────────────────────────────────┐
│        Performance Results                              │
├─────────────────────────────────────────────────────────┤
│  Implementation  │    Time (seconds)                    │
├──────────────────┼──────────────────────────────────────┤
│  List            │    {list_time:.4f}                   │
│  Deque           │    {deque_time:.4f}                  │
├──────────────────┼──────────────────────────────────────┤
│  Winner: {'List' if list_time < deque_time else 'Deque'}│
└─────────────────────────────────────────────────────────┘

🎯 Memory Usage Comparison:
    List:  May need reallocation (memory spikes)
    Deque: Consistent memory usage (no reallocation)
    """)
```

### 📈 When to Use Each Implementation

```
┌─────────────────────────────────────────────────────────────┐
│                    Implementation Guide                     │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  🟢 Use LIST when:                                          │
│     • Learning/prototyping                                  │
│     • Small to medium datasets                              │
│     • Need familiar interface                               │
│     • Single-threaded application                           │
│                                                             │
│  🔵 Use DEQUE when:                                         │
│     • High-performance requirements                         │
│     • Large datasets                                        │
│     • Memory efficiency is important                        │
│     • Consistent operation timing needed                    │
│                                                             │
│  🟡 Use LIFOQUEUE when:                                     │
│     • Multi-threaded environment                            │
│     • Thread safety is critical                             │
│     • Need timeout functionality                            │
│     • Can afford slight performance overhead                │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 💡 Real-World Applications

### 🌍 Common Use Cases with Visual Examples

#### 1. 🔄 Undo Operations in Text Editors

```python
class UndoRedoSystem:
    """Implementing undo/redo using stacks"""
    
    def __init__(self):
        self.undo_stack = []
        self.redo_stack = []
        self.text = ""
    
    def add_text(self, new_text):
        # Save current state for undo
        self.undo_stack.append(self.text)
        self.text = new_text
        # Clear redo stack when new action is performed
        self.redo_stack.clear()
        self.visualize_stacks()
    
    def undo(self):
        if self.undo_stack:
            # Move current state to redo stack
            self.redo_stack.append(self.text)
            # Restore previous state
            self.text = self.undo_stack.pop()
        self.visualize_stacks()
    
    def redo(self):
        if self.redo_stack:
            # Move current state to undo stack
            self.undo_stack.append(self.text)
            # Restore redo state
            self.text = self.redo_stack.pop()
        self.visualize_stacks()
    
    def visualize_stacks(self):
        print(f"\n📝 Current Text: '{self.text}'")
        print("┌─────────────┬─────────────┐")
        print("│ Undo Stack  │ Redo Stack  │")
        print("├─────────────┼─────────────┤")
        
        max_len = max(len(self.undo_stack), len(self.redo_stack), 1)
        for i in range(max_len-1, -1, -1):
            undo_item = self.undo_stack[i] if i < len(self.undo_stack) else ""
            redo_item = self.redo_stack[i] if i < len(self.redo_stack) else ""
            print(f"│ {undo_item:^11} │ {redo_item:^11} │")
        print("└─────────────┴─────────────┘")

# Demo
editor = UndoRedoSystem()
editor.add_text("Hello")
editor.add_text("Hello World")
editor.add_text("Hello World!")
editor.undo()  # Back to "Hello World"
editor.undo()  # Back to "Hello"
editor.redo()  # Forward to "Hello World"
```

#### 2. 🧮 Expression Evaluation (Calculator)

```python
def evaluate_postfix(expression):
    """Evaluate postfix expression using stack"""
    stack = []
    
    print(f"🧮 Evaluating: {expression}")
    print("\nStep-by-step evaluation:")
    
    for token in expression.split():
        if token.isdigit():
            stack.append(int(token))
            print(f"Push {token}: {stack}")
        else:
            # Operator
            b = stack.pop()
            a = stack.pop()
            
            if token == '+':
                result = a + b
            elif token == '-':
                result = a - b
            elif token == '*':
                result = a * b
            elif token == '/':
                result = a // b
            
            stack.append(result)
            print(f"Calculate {a} {token} {b} = {result}: {stack}")
    
    return stack[0]

# Example: "3 4 + 2 *" = (3 + 4) * 2 = 14
result = evaluate_postfix("3 4 + 2 *")
print(f"\n🎯 Final Result: {result}")

# Visual trace:
"""
Expression: 3 4 + 2 *
┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐
│    3    │    │    4    │    │    7    │    │   14    │
└─────────┘    │    3    │    │  (3+4)  │    │ (7*2)   │
Step 1         └─────────┘    └─────────┘    └─────────┘
               Step 2         Step 3         Step 4
"""
```

#### 3. 🔍 Browser History Navigation

```python
class BrowserHistory:
    """Browser navigation using stacks"""
    
    def __init__(self):
        self.history = []
        self.forward_stack = []
        self.current_page = "home"
    
    def visit(self, page):
        """Visit a new page"""
        self.history.append(self.current_page)
        self.current_page = page
        self.forward_stack.clear()  # Clear forward history
        self.display_navigation()
    
    def back(self):
        """Go back to previous page"""
        if self.history:
            self.forward_stack.append(self.current_page)
            self.current_page = self.history.pop()
        self.display_navigation()
    
    def forward(self):
        """Go forward to next page"""
        if self.forward_stack:
            self.history.append(self.current_page)
            self.current_page = self.forward_stack.pop()
        self.display_navigation()
    
    def display_navigation(self):
        print(f"\n🌐 Current Page: {self.current_page}")
        print("┌─────────────────┬─────────────────┐")
        print("│   Back Stack    │  Forward Stack  │")
        print("├─────────────────┼─────────────────┤")
        
        max_len = max(len(self.history), len(self.forward_stack), 1)
        for i in range(max_len-1, -1, -1):
            back_page = self.history[i] if i < len(self.history) else ""
            forward_page = self.forward_stack[i] if i < len(self.forward_stack) else ""
            print(f"│ {back_page:^15} │ {forward_page:^15} │")
        print("└─────────────────┴─────────────────┘")

# Demo
browser = BrowserHistory()
browser.visit("google.com")
browser.visit("stackoverflow.com")
browser.visit("github.com")
browser.back()    # Return to stackoverflow.com
browser.back()    # Return to google.com  
browser.forward() # Go to stackoverflow.com
```

---

## 🧪 Interactive Examples

### 🎮 Stack-Based Game: Plate Balancer

```python
class PlateBalancer:
    """Fun game demonstrating stack operations"""
    
    def __init__(self):
        self.left_stack = []
        self.right_stack = []
        self.score = 0
    
    def add_plate(self, side, weight):
        """Add a plate to specified side"""
        if side.lower() == 'left':
            self.left_stack.append(weight)
        else:
            self.right_stack.append(weight)
        
        self.update_score()
        self.visualize_balance()
    
    def remove_plate(self, side):
        """Remove top plate from specified side"""
        if side.lower() == 'left' and self.left_stack:
            removed = self.left_stack.pop()
            print(f"Removed plate of weight {removed} from left side")
        elif side.lower() == 'right' and self.right_stack:
            removed = self.right_stack.pop()
            print(f"Removed plate of weight {removed} from right side")
        
        self.update_score()
        self.visualize_balance()
    
    def update_score(self):
        """Calculate balance score"""
        left_total = sum(self.left_stack)
        right_total = sum(self.right_stack)
        balance_diff = abs(left_total - right_total)
        self.score = max(0, 100 - balance_diff)
    
    def visualize_balance(self):
        """ASCII visualization of the balance scale"""
        left_total = sum(self.left_stack)
        right_total = sum(self.right_stack)
        
        print(f"\n⚖️  Balance Scale - Score: {self.score}/100")
        print("=" * 50)
        
        # Display stacks
        max_height = max(len(self.left_stack), len(self.right_stack), 1)
        
        for i in range(max_height-1, -1, -1):
            left_plate = f"[{self.left_stack[i]}]" if i < len(self.left_stack) else "   "
            right_plate = f"[{self.right_stack[i]}]" if i < len(self.right_stack) else "   "
            print(f"    {left_plate:^6}     │     {right_plate:^6}")
        
        # Balance beam
        if left_total > right_total:
            print("     \\____    │    ____/")
            print("          \\   │   /")
            print("           \\  │  /")
            print("            \\ │ /")
            print("             \\│/")
        elif right_total > left_total:
            print("     ____/    │    \\____")
            print("         /    │    \\")
            print("        /     │     \\")
            print("       /      │      \\")
            print("      /       │       \\")
        else:
            print("     ─────    │    ─────")
            print("              │")
            print("              │")
            print("          BALANCED!")
        
        print(f"\nLeft Total: {left_total}    Right Total: {right_total}")
        
        if self.score == 100:
            print("🎉 PERFECT BALANCE ACHIEVED! 🎉")

# Game Demo
game = PlateBalancer()
print("🎮 Welcome to Plate Balancer!")
print("Try to balance the scale by adding plates of different weights")

game.add_plate('left', 5)
game.add_plate('right', 3)
game.add_plate('left', 2)
game.add_plate('right', 4)
```

### 🔧 Stack-Based Algorithm: Parentheses Validator

```python
def validate_parentheses(expression):
    """Validate if parentheses are properly balanced"""
    stack = []
    opening = {'(', '[', '{'}
    closing = {')', ']', '}'}
    pairs = {'(': ')', '[': ']', '{': '}'}
    
    print(f"🔍 Validating: {expression}")
    print("\nStep-by-step analysis:")
    print("┌─────┬─────────┬─────────────────┐")
    print("│Char │  Stack  │     Action      │")
    print("├─────┼─────────┼─────────────────┤")
    
    for i, char in enumerate(expression):
        if char in opening:
            stack.append(char)
            print(f"│ {char:^3} │ {str(stack):^7} │ Push opening    │")
        elif char in closing:
            if not stack:
                print(f"│ {char:^3} │ {str(stack):^7} │ ERROR: No match │")
                print("└─────┴─────────┴─────────────────┘")
                return False
            
            top = stack.pop()
            if pairs[top] == char:
                print(f"│ {char:^3} │ {str(stack):^7} │ Match found!    │")
            else:
                print(f"│ {char:^3} │ {str(stack):^7} │ ERROR: Mismatch │")
                print("└─────┴─────────┴─────────────────┘")
                return False
    
    print("└─────┴─────────┴─────────────────┘")
    
    is_valid = len(stack) == 0
    print(f"\n{'✅ VALID' if is_valid else '❌ INVALID'}: Final stack is {'empty' if is_valid else 'not empty'}")
    
    if stack:
        print(f"Unmatched opening brackets: {stack}")
    
    return is_valid

# Test cases
test_expressions = [
    "((()))",           # Valid
    "([{}])",          # Valid  
    "([)]",            # Invalid - wrong order
    "(((",             # Invalid - unmatched opening
    ")))",             # Invalid - unmatched closing
]

for expr in test_expressions:
    validate_parentheses(expr)
    print("\n" + "="*50 + "\n")
```

---

## 📊 Best Practices

### ✨ Professional Stack Implementation

```python
from typing import Generic, TypeVar, Optional, List
from collections import deque

T = TypeVar('T')

class ProfessionalStack(Generic[T]):
    """
    Professional-grade stack implementation with type hints,
    error handling, and comprehensive functionality.
    """
    
    def __init__(self, max_size: Optional[int] = None):
        """
        Initialize stack with optional size limit.
        
        Args:
            max_size: Maximum number of elements (None for unlimited)
        """
        self._items: deque[T] = deque()
        self._max_size = max_size
    
    def push(self, item: T) -> None:
        """
        Add item to top of stack.
        
        Args:
            item: Item to add to stack
            
        Raises:
            OverflowError: If stack is at maximum capacity
        """
        if self._max_size and len(self._items) >= self._max_size:
            raise OverflowError(f"Stack overflow: Cannot exceed {self._max_size} items")
        
        self._items.append(item)
    
    def pop(self) -> T:
        """
        Remove and return top item from stack.
        
        Returns:
            Top item from stack
            
        Raises:
            IndexError: If stack is empty
        """
        if self.is_empty():
            raise IndexError("Stack underflow: Cannot pop from empty stack")
        
        return self._items.pop()
    
    def peek(self) -> T:
        """
        Return top item without removing it.
        
        Returns:
            Top item from stack
            
        Raises:
            IndexError: If stack is empty
        """
        if self.is_empty():
            raise IndexError("Cannot peek at empty stack")
        
        return self._items[-1]
    
    def is_empty(self) -> bool:
        """Check if stack is empty."""
        return len(self._items) == 0
    
    def is_full(self) -> bool:
        """Check if stack is at maximum capacity."""
        if self._max_size is None:
            return False
        return len(self._items) >= self._max_size
    
    def size(self) -> int:
        """Return number of items in stack."""
        return len(self._items)
    
    def clear(self) -> None:
        """Remove all items from stack."""
        self._items.clear()
    
    def to_list(self) -> List[T]:
        """Return stack contents as list (top to bottom)."""
        return list(reversed(self._items))
    
    def __str__(self) -> str:
        """String representation of stack."""
        items_str = ', '.join(str(item) for item in reversed(self._items))
        return f"Stack([{items_str}]) ← top"
    
    def __len__(self) -> int:
        """Return stack size."""
        return len(self._items)
    
    def __bool__(self) -> bool:
        """Return True if stack is not empty."""
        return not self.is_empty()

# Example usage with type safety
stack: ProfessionalStack[str] = ProfessionalStack(max_size=5)

try:
    stack.push("first")
    stack.push("second")
    stack.push("third")
    print(f"Stack: {stack}")
    print(f"Size: {len(stack)}")
    print(f"Top: {stack.peek()}")
    print(f"Popped: {stack.pop()}")
    print(f"After pop: {stack}")
except (OverflowError, IndexError) as e:
    print(f"Error: {e}")
```

### 🎯 Error Handling Best Practices

```python
class RobustStack:
    """Stack with comprehensive error handling and logging"""
    
    def __init__(self):
        self.items = []
        self._operation_count = 0
        self._max_operations = 1000  # Prevent infinite operations
    
    def _check_operation_limit(self):
        """Prevent runaway operations"""
        self._operation_count += 1
        if self._operation_count > self._max_operations:
            raise RuntimeError("Operation limit exceeded")
    
    def safe_push(self, item):
        """Push with error handling"""
        try:
            self._check_operation_limit()
            if item is None:
                raise ValueError("Cannot push None to stack")
            self.items.append(item)
            return True
        except Exception as e:
            print(f"❌ Push failed: {e}")
            return False
    
    def safe_pop(self):
        """Pop with error handling"""
        try:
            self._check_operation_limit()
            if not self.items:
                raise IndexError("Stack is empty")
            return self.items.pop(), True
        except Exception as e:
            print(f"❌ Pop failed: {e}")
            return None, False
    
    def safe_peek(self):
        """Peek with error handling"""
        try:
            if not self.items:
                return None, "Stack is empty"
            return self.items[-1], "Success"
        except Exception as e:
            return None, f"Error: {e}"

# Demonstration of error handling
robust_stack = RobustStack()

print("🛡️ Robust Stack Demonstration:")
print(f"Push 'test': {robust_stack.safe_push('test')}")
print(f"Push None: {robust_stack.safe_push(None)}")
print(f"Peek: {robust_stack.safe_peek()}")

# Pop from empty stack
robust_stack.safe_pop()  # Remove 'test'
result, success = robust_stack.safe_pop()  # Try to pop from empty stack
print(f"Pop from empty: Success={success}, Result={result}")
```

---

## 🎓 Summary and Key Takeaways

### 🌟 What You've Learned

```
┌─────────────────────────────────────────────────────────────┐
│                    🎉 Congratulations! 🎉                   │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  You've mastered Python Stacks! Here's what you learned:    │
│                                                             │
│  ✅ LIFO Principle and Stack Fundamentals                   │
│  ✅ Core Operations (Push, Pop, Peek, etc.)                 │
│  ✅ Multiple Implementation Methods                         │
│  ✅ Performance Characteristics and Trade-offs              │
│  ✅ Real-World Applications and Use Cases                   │
│  ✅ Professional Coding Practices                           │
│  ✅ Error Handling and Robustness                           │
│                                                             │
│  📚 Next Steps:                                             │
│     • Practice with LeetCode stack problems                 │
│     • Explore advanced data structures (queues, trees)      │
│     • Build your own stack-based applications               │
│     • Study algorithm time/space complexity                 │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 🔗 Quick Reference Card

```python
# 🚀 Quick Stack Operations Reference

# Method 1: Using List (Simple)
stack = []
stack.append(item)      # Push
item = stack.pop()      # Pop  
top = stack[-1]         # Peek
empty = len(stack) == 0 # Check empty

# Method 2: Using Deque (Performance)
from collections import deque
stack = deque()
stack.append(item)      # Push
item = stack.pop()      # Pop
top = stack[-1]         # Peek
empty = len(stack) == 0 # Check empty

# Method 3: Thread-Safe (Multi-threading)
from queue import LifoQueue
stack = LifoQueue()
stack.put(item)         # Push
item = stack.get()      # Pop (blocking)
empty = stack.empty()   # Check empty
```

### 🎯 Remember the Stack Mantra:
> **"Last In, First Out - The top is where the action happens!"**

---

*Happy coding! 🐍✨*

---

### 📖 Additional Resources

- **Real Python Stack Guide**: [realpython.com/how-to-implement-python-stack/](https://realpython.com/how-to-implement-python-stack/)
- **Python Documentation**: [docs.python.org/3/library/collections.html#collections.deque](https://docs.python.org/3/library/collections.html#collections.deque)
- **Interactive Visualizer**: [pythontutor.com](http://pythontutor.com)
- **Practice Problems**: [leetcode.com/tag/stack/](https://leetcode.com/tag/stack/)

---

*This guide was created with ❤️ for Python developers who want to master stack data structures!*