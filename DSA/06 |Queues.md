# 🚀 Python Queues: The Complete Interactive Guide

> **Master the art of First-In, First-Out (FIFO) data structures with visual representations, practical examples, and real-world applications**

[![Python Queues](https://img.shields.io/badge/Python-Queues-blue?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
![Topic](https://img.shields.io/badge/Topic-Data%20Structures-green?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-Beginner%20to%20Advanced-orange?style=for-the-badge)


---

## 📋 Table of Contents

- [🎯 What is a Queue?](#-what-is-a-queue)
- [🔧 Core Queue Operations](#-core-queue-operations)
- [🎨 Visual ASCII Representations](#-visual-ascii-representations)
- [💻 Python Queue Implementations](#-python-queue-implementations)
  - [Method 1: Using Python Lists](#method-1-using-python-lists)
  - [Method 2: Using collections.deque](#method-2-using-collectionsdeque)
  - [Method 3: Using queue.Queue](#method-3-using-queuequeue)
  - [Method 4: Custom Queue Class](#method-4-custom-queue-class)
- [🏗️ Building Advanced Queue Types](#️-building-advanced-queue-types)
- [🌟 Real-World Applications](#-real-world-applications)
- [📊 Performance Comparison](#-performance-comparison)
- [🧪 Interactive Code Examples](#-interactive-code-examples)
- [🎮 Practice Challenges](#-practice-challenges)
- [📚 Summary & Best Practices](#-summary--best-practices)

---

## 🎯 What is a Queue?

A **Queue** is a linear data structure that follows the **FIFO (First In, First Out)** principle. Think of it like a real-world queue at a coffee shop - the first person in line is the first person to be served!

### 🎭 Real-World Analogy

```
    🧑‍💼 ← 👩‍🔬 ← 👨‍🎓 ← 👵 ← 👶
   (Exit)              (Enter)
   First                Last
   Out                  In
```

**Key Characteristics:**
- ✅ **FIFO Principle**: First element added is the first to be removed
- ✅ **Two Ends**: Front (for removal) and Rear (for insertion)
- ✅ **Linear Structure**: Elements arranged in sequential order
- ✅ **Dynamic Size**: Can grow and shrink during runtime

---

## 🔧 Core Queue Operations

### Essential Operations

| Operation | Description | Time Complexity | Visual |
|-----------|-------------|-----------------|---------|
| **Enqueue** | Add element to rear | O(1) | `[A, B, C] → [A, B, C, D]` |
| **Dequeue** | Remove element from front | O(1) | `[A, B, C] → [B, C]` |
| **Peek/Front** | View front element | O(1) | `[A, B, C] → A` |
| **IsEmpty** | Check if queue is empty | O(1) | `[] → True` |
| **Size** | Get number of elements | O(1) | `[A, B, C] → 3` |

### 🎯 Interactive Operations Demonstration

```python
# Let's trace through queue operations step by step
queue_demo = []

print("📥 ENQUEUE Operations:")
queue_demo.append('🍎')  # Enqueue Apple
print(f"After adding 🍎: {queue_demo}")

queue_demo.append('🍌')  # Enqueue Banana
print(f"After adding 🍌: {queue_demo}")

queue_demo.append('🍊')  # Enqueue Orange
print(f"After adding 🍊: {queue_demo}")

print("\n📤 DEQUEUE Operations:")
first_item = queue_demo.pop(0)  # Dequeue
print(f"Removed: {first_item}, Queue: {queue_demo}")

second_item = queue_demo.pop(0)  # Dequeue
print(f"Removed: {second_item}, Queue: {queue_demo}")
```

**Expected Output:**
```
📥 ENQUEUE Operations:
After adding 🍎: ['🍎']
After adding 🍌: ['🍎', '🍌']
After adding 🍊: ['🍎', '🍌', '🍊']

📤 DEQUEUE Operations:
Removed: 🍎, Queue: ['🍌', '🍊']
Removed: 🍌, Queue: ['🍊']
```

---

## 🎨 Visual ASCII Representations

### 📊 Queue Structure Visualization

```
    FRONT                           REAR
      ↓                              ↓
   ┌─────┬─────┬─────┬─────┬─────┬─────┐
   │  A  │  B  │  C  │  D  │  E  │  F  │
   └─────┴─────┴─────┴─────┴─────┴─────┘
      ↑                              ↑
   DEQUEUE                       ENQUEUE
   (Remove)                      (Add)
```

### 🔄 FIFO Operation Flow

```
Initial Queue:
┌─────────────────────────────┐
│  EMPTY QUEUE                │
└─────────────────────────────┘

After ENQUEUE(10):
┌─────┐
│ 10  │ ← REAR
└─────┘
  ↑
FRONT

After ENQUEUE(20):
┌─────┬─────┐
│ 10  │ 20  │ ← REAR
└─────┴─────┘
  ↑
FRONT

After ENQUEUE(30):
┌─────┬─────┬─────┐
│ 10  │ 20  │ 30  │ ← REAR
└─────┴─────┴─────┘
  ↑
FRONT

After DEQUEUE():
         ┌─────┬─────┐
Removed: │ 20  │ 30  │ ← REAR
   10    └─────┴─────┘
           ↑
         FRONT
```

### 🎭 Queue States Visualization

```
📊 QUEUE STATES:

🔹 Empty Queue:
   ┌─────────┐
   │ EMPTY   │
   └─────────┘
   Front = Rear = -1

🔹 Single Element:
   ┌─────┐
   │  X  │ ← Front & Rear
   └─────┘

🔹 Multiple Elements:
   ┌─────┬─────┬─────┬─────┐
   │  A  │  B  │  C  │  D  │
   └─────┴─────┴─────┴─────┘
     ↑                   ↑
   Front               Rear

🔹 Full Queue (Bounded):
   ┌─────┬─────┬─────┬─────┬─────┐
   │  A  │  B  │  C  │  D  │  E  │  ← Max Capacity
   └─────┴─────┴─────┴─────┴─────┘
     ↑                         ↑
   Front                     Rear
```

---

## 💻 Python Queue Implementations

### Method 1: Using Python Lists

```python
"""
🟡 Using Lists for Queue Implementation
Pros: Simple, built-in
Cons: O(n) dequeue operation due to element shifting
"""

class ListQueue:
    def __init__(self):
        """Initialize empty queue using Python list"""
        self.queue = []
    
    def enqueue(self, item):
        """Add item to rear of queue - O(1)"""
        self.queue.append(item)
        print(f"✅ Enqueued: {item}")
    
    def dequeue(self):
        """Remove item from front of queue - O(n)"""
        if self.is_empty():
            print("❌ Queue is empty!")
            return None
        item = self.queue.pop(0)  # O(n) operation!
        print(f"📤 Dequeued: {item}")
        return item
    
    def peek(self):
        """View front item without removing - O(1)"""
        if self.is_empty():
            return None
        return self.queue[0]
    
    def is_empty(self):
        """Check if queue is empty - O(1)"""
        return len(self.queue) == 0
    
    def size(self):
        """Get queue size - O(1)"""
        return len(self.queue)
    
    def display(self):
        """Display queue contents"""
        print(f"📋 Queue: {self.queue}")

# 🧪 Interactive Demo
print("🚀 List-Based Queue Demo")
print("=" * 30)

my_queue = ListQueue()
my_queue.display()

# Enqueue operations
my_queue.enqueue("Task 1")
my_queue.enqueue("Task 2")
my_queue.enqueue("Task 3")
my_queue.display()

print(f"👀 Front item: {my_queue.peek()}")
print(f"📏 Queue size: {my_queue.size()}")

# Dequeue operations
my_queue.dequeue()
my_queue.dequeue()
my_queue.display()
```

### Method 2: Using collections.deque

```python
"""
🟢 Using collections.deque for Queue Implementation
Pros: O(1) operations at both ends, memory efficient
Cons: Slightly more complex than lists
"""

from collections import deque

class DequeQueue:
    def __init__(self):
        """Initialize queue using collections.deque"""
        self.queue = deque()
    
    def enqueue(self, item):
        """Add item to rear - O(1)"""
        self.queue.append(item)
        print(f"✅ Enqueued: {item}")
    
    def dequeue(self):
        """Remove item from front - O(1)"""
        if self.is_empty():
            print("❌ Queue is empty!")
            return None
        item = self.queue.popleft()  # O(1) operation!
        print(f"📤 Dequeued: {item}")
        return item
    
    def peek(self):
        """View front item - O(1)"""
        if self.is_empty():
            return None
        return self.queue[0]
    
    def is_empty(self):
        """Check if empty - O(1)"""
        return len(self.queue) == 0
    
    def size(self):
        """Get size - O(1)"""
        return len(self.queue)
    
    def display(self):
        """Display queue with visual representation"""
        if self.is_empty():
            print("📋 Queue: EMPTY")
        else:
            queue_visual = " → ".join(str(item) for item in self.queue)
            print(f"📋 Queue: {queue_visual}")
            print(f"      Front: {self.queue[0]} | Rear: {self.queue[-1]}")

# 🧪 Interactive Demo
print("\n🚀 Deque-Based Queue Demo")
print("=" * 30)

efficient_queue = DequeQueue()

# Performance test with visual feedback
items = ["🎵 Audio Task", "📁 File Task", "🌐 Network Task", "💾 Save Task"]

for item in items:
    efficient_queue.enqueue(item)
    efficient_queue.display()
    print()

print("🔄 Processing queue...")
while not efficient_queue.is_empty():
    efficient_queue.dequeue()
    efficient_queue.display()
    print()
```

### Method 3: Using queue.Queue

```python
"""
🔵 Using queue.Queue for Thread-Safe Implementation
Pros: Thread-safe, blocking operations, maxsize support
Cons: Designed for multi-threading, slightly heavier
"""

import queue
import threading
import time

def demonstrate_queue_module():
    """Demonstrate queue.Queue with thread safety"""
    
    # Create bounded queue
    task_queue = queue.Queue(maxsize=3)
    
    print("🚀 Thread-Safe Queue Demo")
    print("=" * 30)
    
    # Enqueue with size limits
    print("📥 Adding tasks to bounded queue (max 3):")
    try:
        task_queue.put("Task A", block=False)
        print(f"✅ Added: Task A | Size: {task_queue.qsize()}")
        
        task_queue.put("Task B", block=False)
        print(f"✅ Added: Task B | Size: {task_queue.qsize()}")
        
        task_queue.put("Task C", block=False)
        print(f"✅ Added: Task C | Size: {task_queue.qsize()}")
        
        print(f"🔍 Queue full? {task_queue.full()}")
        
        # This will raise exception if queue is full
        # task_queue.put("Task D", block=False)  # Would raise queue.Full
        
    except queue.Full:
        print("❌ Queue is full!")
    
    print("\n📤 Removing tasks:")
    while not task_queue.empty():
        task = task_queue.get()
        print(f"✅ Removed: {task} | Remaining: {task_queue.qsize()}")
        task_queue.task_done()  # Mark task as completed
    
    print(f"🔍 Queue empty? {task_queue.empty()}")

# Producer-Consumer Demo
def producer(q, producer_id):
    """Producer function for threading demo"""
    for i in range(3):
        item = f"Item-{producer_id}-{i+1}"
        q.put(item)
        print(f"🏭 Producer {producer_id} created: {item}")
        time.sleep(0.1)

def consumer(q, consumer_id):
    """Consumer function for threading demo"""
    for i in range(3):
        item = q.get()
        print(f"🛒 Consumer {consumer_id} processed: {item}")
        q.task_done()
        time.sleep(0.15)

def threading_demo():
    """Demonstrate queue in multi-threading"""
    print("\n🧵 Multi-Threading Queue Demo")
    print("=" * 35)
    
    shared_queue = queue.Queue()
    
    # Create and start threads
    producer_thread = threading.Thread(target=producer, args=(shared_queue, 1))
    consumer_thread = threading.Thread(target=consumer, args=(shared_queue, 1))
    
    producer_thread.start()
    consumer_thread.start()
    
    # Wait for threads to complete
    producer_thread.join()
    consumer_thread.join()
    
    print("✅ All threads completed!")

# Run demonstrations
demonstrate_queue_module()
threading_demo()
```

### Method 4: Custom Queue Class

```python
"""
🟠 Custom Queue Implementation with Visual Features
Pros: Full control, educational, customizable
Cons: Need to implement everything from scratch
"""

class VisualQueue:
    def __init__(self, max_size=None):
        """Initialize custom queue with optional size limit"""
        self.items = []
        self.max_size = max_size
        self.front = 0
        self.rear = -1
        self.count = 0
    
    def enqueue(self, item):
        """Add item with visual feedback"""
        if self.is_full():
            print(f"❌ Queue is full! Cannot add {item}")
            return False
        
        self.items.append(item)
        self.rear += 1
        self.count += 1
        
        print(f"✅ Enqueued: {item}")
        self._visualize()
        return True
    
    def dequeue(self):
        """Remove item with visual feedback"""
        if self.is_empty():
            print("❌ Queue is empty!")
            return None
        
        item = self.items[self.front]
        self.front += 1
        self.count -= 1
        
        # Reset pointers when queue becomes empty
        if self.count == 0:
            self.front = 0
            self.rear = -1
            self.items = []
        
        print(f"📤 Dequeued: {item}")
        self._visualize()
        return item
    
    def peek(self):
        """View front item"""
        if self.is_empty():
            return None
        return self.items[self.front]
    
    def is_empty(self):
        """Check if queue is empty"""
        return self.count == 0
    
    def is_full(self):
        """Check if queue is full"""
        if self.max_size is None:
            return False
        return self.count >= self.max_size
    
    def size(self):
        """Get current size"""
        return self.count
    
    def _visualize(self):
        """Create ASCII visualization of queue state"""
        if self.is_empty():
            print("📋 Queue: [ EMPTY ]")
            return
        
        # Get active items (from front to rear)
        active_items = self.items[self.front:self.rear+1]
        
        # Create visual representation
        if len(active_items) == 1:
            print(f"📋 Queue: [ {active_items[0]} ]")
            print("         FRONT & REAR")
        else:
            visual = " | ".join(str(item) for item in active_items)
            print(f"📋 Queue: [ {visual} ]")
            
            # Add pointers
            front_pointer = "FRONT" + " " * (len(str(active_items[0])) - 2)
            rear_spaces = " " * (len(visual) - len(str(active_items[-1])) + 2)
            rear_pointer = rear_spaces + "REAR"
            
            print(f"         {front_pointer}{rear_pointer}")
        
        print(f"📊 Stats: Size={self.size()}, Front={self.front}, Rear={self.rear}")
        print("-" * 50)

# 🎮 Interactive Custom Queue Demo
def custom_queue_demo():
    """Interactive demonstration of custom queue"""
    print("🎨 Custom Visual Queue Demo")
    print("=" * 40)
    
    # Create queue with size limit
    vq = VisualQueue(max_size=4)
    
    print("🎯 Testing Queue Operations:")
    print("=" * 30)
    
    # Test enqueue operations
    test_items = ["🎵 Song", "📷 Photo", "📄 Document", "🎥 Video"]
    
    for item in test_items:
        vq.enqueue(item)
        print(f"👀 Front item: {vq.peek()}")
        print()
    
    # Try to add one more (should fail)
    vq.enqueue("🎮 Game")
    
    print("\n🔄 Processing queue:")
    print("=" * 20)
    
    # Process all items
    while not vq.is_empty():
        print(f"👀 About to process: {vq.peek()}")
        vq.dequeue()
        print()

# Run the demo
custom_queue_demo()
```

---

## 🏗️ Building Advanced Queue Types

### 🔄 Circular Queue Implementation

```python
"""
🎡 Circular Queue - Efficient Space Utilization
Reuses empty spaces at the front when items are dequeued
"""

class CircularQueue:
    def __init__(self, capacity):
        """Initialize circular queue with fixed capacity"""
        self.capacity = capacity
        self.queue = [None] * capacity
        self.front = -1
        self.rear = -1
        self.size = 0
    
    def enqueue(self, item):
        """Add item to circular queue"""
        if self.is_full():
            print(f"❌ Circular queue is full! Cannot add {item}")
            return False
        
        if self.is_empty():
            self.front = 0
            self.rear = 0
        else:
            self.rear = (self.rear + 1) % self.capacity
        
        self.queue[self.rear] = item
        self.size += 1
        
        print(f"✅ Added {item} at position {self.rear}")
        self._visualize_circular()
        return True
    
    def dequeue(self):
        """Remove item from circular queue"""
        if self.is_empty():
            print("❌ Circular queue is empty!")
            return None
        
        item = self.queue[self.front]
        self.queue[self.front] = None
        
        if self.size == 1:
            self.front = -1
            self.rear = -1
        else:
            self.front = (self.front + 1) % self.capacity
        
        self.size -= 1
        
        print(f"📤 Removed {item}")
        self._visualize_circular()
        return item
    
    def is_empty(self):
        return self.size == 0
    
    def is_full(self):
        return self.size == self.capacity
    
    def _visualize_circular(self):
        """Visualize circular queue structure"""
        print("🎡 Circular Queue State:")
        
        # Create circular visualization
        visual = []
        for i in range(self.capacity):
            if self.queue[i] is not None:
                if i == self.front and i == self.rear:
                    visual.append(f"[{self.queue[i]}]F&R")
                elif i == self.front:
                    visual.append(f"[{self.queue[i]}]F")
                elif i == self.rear:
                    visual.append(f"[{self.queue[i]}]R")
                else:
                    visual.append(f"[{self.queue[i]}]")
            else:
                visual.append("[ ]")
        
        # Print in circular format
        print("   " + " - ".join(visual))
        print(f"   Size: {self.size}/{self.capacity}")
        print("-" * 50)

# Demo circular queue
def circular_queue_demo():
    print("🎡 Circular Queue Demonstration")
    print("=" * 40)
    
    cq = CircularQueue(5)
    
    # Fill the queue
    items = ["A", "B", "C", "D", "E"]
    for item in items:
        cq.enqueue(item)
    
    # Try to add one more
    cq.enqueue("F")
    
    # Remove some items
    print("\n🔄 Removing items:")
    cq.dequeue()
    cq.dequeue()
    
    # Add new items (should reuse space)
    print("\n➕ Adding new items:")
    cq.enqueue("F")
    cq.enqueue("G")

circular_queue_demo()
```

### 🏆 Priority Queue Implementation

```python
"""
🏆 Priority Queue - Elements with Priorities
Higher priority items are dequeued first
"""

import heapq
from dataclasses import dataclass
from typing import Any

@dataclass
class PriorityItem:
    priority: int
    item: Any
    
    def __lt__(self, other):
        return self.priority > other.priority  # Higher number = higher priority

class PriorityQueue:
    def __init__(self):
        """Initialize priority queue"""
        self.heap = []
        self.entry_finder = {}
        self.counter = 0
    
    def enqueue(self, item, priority):
        """Add item with priority"""
        if item in self.entry_finder:
            self.remove(item)
        
        entry = PriorityItem(priority, item)
        self.entry_finder[item] = entry
        heapq.heappush(self.heap, entry)
        self.counter += 1
        
        print(f"✅ Added {item} with priority {priority}")
        self._visualize_priority()
    
    def dequeue(self):
        """Remove highest priority item"""
        while self.heap:
            entry = heapq.heappop(self.heap)
            if entry.item in self.entry_finder:
                del self.entry_finder[entry.item]
                print(f"📤 Removed {entry.item} (priority: {entry.priority})")
                self._visualize_priority()
                return entry.item
        
        print("❌ Priority queue is empty!")
        return None
    
    def remove(self, item):
        """Remove specific item"""
        if item in self.entry_finder:
            del self.entry_finder[item]
    
    def is_empty(self):
        return len(self.entry_finder) == 0
    
    def _visualize_priority(self):
        """Visualize priority queue"""
        if self.is_empty():
            print("📋 Priority Queue: EMPTY")
            return
        
        # Sort by priority for display
        items = sorted(self.entry_finder.values(), 
                      key=lambda x: x.priority, reverse=True)
        
        print("📋 Priority Queue (High → Low):")
        for entry in items:
            print(f"   🔸 {entry.item} (P:{entry.priority})")
        print("-" * 40)

# Demo priority queue
def priority_queue_demo():
    print("🏆 Priority Queue Demonstration")
    print("=" * 40)
    
    pq = PriorityQueue()
    
    # Add tasks with different priorities
    tasks = [
        ("🚨 Critical Bug Fix", 10),
        ("📧 Send Email", 3),
        ("🔧 Code Review", 7),
        ("☕ Coffee Break", 1),
        ("🚀 Deploy Release", 9),
        ("📚 Documentation", 4)
    ]
    
    print("➕ Adding tasks:")
    for task, priority in tasks:
        pq.enqueue(task, priority)
    
    print("\n🔄 Processing tasks by priority:")
    while not pq.is_empty():
        task = pq.dequeue()
        print(f"🔧 Processing: {task}")
        print()

priority_queue_demo()
```

---

## 🌟 Real-World Applications

### 1. 🖨️ Print Job Scheduler

```python
"""
🖨️ Print Job Management System
Demonstrates FIFO queue in printer spooling
"""

import time
from datetime import datetime
from collections import deque

class PrintJob:
    def __init__(self, document, user, pages):
        self.document = document
        self.user = user
        self.pages = pages
        self.timestamp = datetime.now()
        self.job_id = f"PJ{int(time.time() * 1000) % 10000}"
    
    def __str__(self):
        return f"{self.job_id}: {self.document} ({self.pages}p) - {self.user}"

class PrintQueue:
    def __init__(self):
        self.queue = deque()
        self.current_job = None
    
    def add_job(self, document, user, pages):
        """Add new print job to queue"""
        job = PrintJob(document, user, pages)
        self.queue.append(job)
        print(f"📝 Job added: {job}")
        self._display_queue()
    
    def process_next_job(self):
        """Process next job in queue"""
        if not self.queue:
            print("✅ No jobs in queue")
            return None
        
        self.current_job = self.queue.popleft()
        print(f"🖨️ Printing: {self.current_job}")
        
        # Simulate printing time (1 sec per page)
        for page in range(1, self.current_job.pages + 1):
            print(f"   📄 Printing page {page}/{self.current_job.pages}")
            time.sleep(0.2)  # Reduced for demo
        
        print(f"✅ Job completed: {self.current_job.job_id}")
        self.current_job = None
        self._display_queue()
    
    def _display_queue(self):
        """Display current queue status"""
        print(f"\n🖨️ Print Queue Status ({len(self.queue)} jobs pending):")
        if self.current_job:
            print(f"   🔄 Currently printing: {self.current_job}")
        
        for i, job in enumerate(self.queue, 1):
            print(f"   {i}. {job}")
        print("-" * 50)

# Demo print queue system
def print_queue_demo():
    print("🖨️ Print Job Scheduler Demo")
    print("=" * 40)
    
    printer = PrintQueue()
    
    # Add several print jobs
    jobs = [
        ("Report.pdf", "Alice", 5),
        ("Presentation.pptx", "Bob", 12),
        ("Invoice.docx", "Charlie", 2),
        ("Manual.pdf", "David", 25),
        ("Memo.txt", "Eve", 1)
    ]
    
    # Add all jobs
    for doc, user, pages in jobs:
        printer.add_job(doc, user, pages)
    
    # Process all jobs
    print("\n🔄 Processing print queue:")
    while printer.queue or printer.current_job:
        printer.process_next_job()
        print()

print_queue_demo()
```

### 2. 🌐 Web Server Request Handling

```python
"""
🌐 Web Server Request Queue
Simulates HTTP request handling with queues
"""

import threading
import queue
import time
import random
from datetime import datetime

class HTTPRequest:
    def __init__(self, method, path, client_ip):
        self.method = method
        self.path = path
        self.client_ip = client_ip
        self.timestamp = datetime.now()
        self.request_id = f"REQ{random.randint(1000, 9999)}"
        self.processing_time = random.uniform(0.1, 0.5)  # Random processing time
    
    def __str__(self):
        return f"{self.request_id}: {self.method} {self.path} from {self.client_ip}"

class WebServerQueue:
    def __init__(self, max_workers=3):
        self.request_queue = queue.Queue()
        self.workers = []
        self.max_workers = max_workers
        self.processed_count = 0
        self.running = True
    
    def start_workers(self):
        """Start worker threads to process requests"""
        for i in range(self.max_workers):
            worker = threading.Thread(
                target=self._worker, 
                args=(f"Worker-{i+1}",),
                daemon=True
            )
            worker.start()
            self.workers.append(worker)
    
    def _worker(self, worker_name):
        """Worker thread function"""
        while self.running:
            try:
                request = self.request_queue.get(timeout=1)
                self._process_request(request, worker_name)
                self.request_queue.task_done()
            except queue.Empty:
                continue
    
    def _process_request(self, request, worker_name):
        """Process HTTP request"""
        print(f"🔄 {worker_name} processing: {request}")
        
        # Simulate request processing
        time.sleep(request.processing_time)
        
        # Simulate response
        status_codes = [200, 200, 200, 404, 500]  # Mostly successful
        status = random.choice(status_codes)
        
        print(f"✅ {worker_name} completed: {request.request_id} -> {status}")
        self.processed_count += 1
        self._display_stats()
    
    def add_request(self, method, path, client_ip):
        """Add new HTTP request to queue"""
        request = HTTPRequest(method, path, client_ip)
        self.request_queue.put(request)
        print(f"📨 New request: {request}")
        print(f"   📊 Queue size: {self.request_queue.qsize()}")
    
    def _display_stats(self):
        """Display server statistics"""
        print(f"   📊 Processed: {self.processed_count}, Pending: {self.request_queue.qsize()}")
    
    def stop(self):
        """Stop the server"""
        self.running = False
        print("🛑 Server stopping...")

# Demo web server queue
def web_server_demo():
    print("🌐 Web Server Request Queue Demo")
    print("=" * 45)
    
    server = WebServerQueue(max_workers=2)
    server.start_workers()
    
    # Simulate incoming requests
    requests = [
        ("GET", "/", "192.168.1.100"),
        ("POST", "/api/users", "10.0.0.1"),
        ("GET", "/images/logo.png", "192.168.1.101"),
        ("GET", "/api/data", "172.16.0.50"),
        ("DELETE", "/api/users/123", "10.0.0.1"),
        ("GET", "/about", "192.168.1.102"),
        ("POST", "/api/login", "203.0.113.1"),
        ("GET", "/favicon.ico", "192.168.1.100"),
    ]
    
    print("📨 Simulating incoming requests:")
    for method, path, ip in requests:
        server.add_request(method, path, ip)
        time.sleep(0.1)  # Slight delay between requests
    
    # Wait for all requests to be processed
    print("\n⏳ Waiting for all requests to be processed...")
    server.request_queue.join()
    
    server.stop()
    print("✅ All requests processed!")

web_server_demo()
```

### 3. 🎮 Game Event System

```python
"""
🎮 Game Event Queue System
Handles player actions and game events in order
"""

from collections import deque
from enum import Enum
import time

class EventType(Enum):
    MOVE = "🚶 Move"
    ATTACK = "⚔️ Attack"
    HEAL = "💚 Heal"
    COLLECT = "🎒 Collect"
    LEVEL_UP = "⭐ Level Up"
    DAMAGE = "💥 Damage"

class GameEvent:
    def __init__(self, event_type, player, target=None, data=None):
        self.event_type = event_type
        self.player = player
        self.target = target
        self.data = data or {}
        self.timestamp = time.time()
    
    def __str__(self):
        if self.target:
            return f"{self.event_type.value}: {self.player} → {self.target}"
        return f"{self.event_type.value}: {self.player}"

class GameEventQueue:
    def __init__(self):
        self.event_queue = deque()
        self.processed_events = []
    
    def add_event(self, event_type, player, target=None, data=None):
        """Add new game event"""
        event = GameEvent(event_type, player, target, data)
        self.event_queue.append(event)
        print(f"📋 Event queued: {event}")
        self._display_queue()
    
    def process_next_event(self):
        """Process next event in queue"""
        if not self.event_queue:
            print("✅ No events to process")
            return None
        
        event = self.event_queue.popleft()
        print(f"\n🎯 Processing: {event}")
        
        # Simulate event processing
        self._execute_event(event)
        self.processed_events.append(event)
        
        self._display_queue()
        return event
    
    def _execute_event(self, event):
        """Execute the game event"""
        if event.event_type == EventType.MOVE:
            print(f"   🚶 {event.player} moved to {event.data.get('position', 'unknown')}")
        
        elif event.event_type == EventType.ATTACK:
            damage = event.data.get('damage', 10)
            print(f"   ⚔️ {event.player} attacks {event.target} for {damage} damage!")
        
        elif event.event_type == EventType.HEAL:
            amount = event.data.get('amount', 20)
            print(f"   💚 {event.player} heals for {amount} HP")
        
        elif event.event_type == EventType.COLLECT:
            item = event.data.get('item', 'item')
            print(f"   🎒 {event.player} collected {item}")
        
        elif event.event_type == EventType.LEVEL_UP:
            level = event.data.get('level', 'unknown')
            print(f"   ⭐ {event.player} leveled up to level {level}!")
        
        elif event.event_type == EventType.DAMAGE:
            damage = event.data.get('damage', 5)
            source = event.data.get('source', 'unknown')
            print(f"   💥 {event.player} takes {damage} damage from {source}")
        
        # Simulate processing time
        time.sleep(0.1)
    
    def _display_queue(self):
        """Display current event queue"""
        print(f"\n🎮 Event Queue ({len(self.event_queue)} pending):")
        for i, event in enumerate(self.event_queue, 1):
            print(f"   {i}. {event}")
        print("-" * 40)
    
    def get_stats(self):
        """Get processing statistics"""
        return {
            'pending': len(self.event_queue),
            'processed': len(self.processed_events),
            'total': len(self.event_queue) + len(self.processed_events)
        }

# Demo game event system
def game_event_demo():
    print("🎮 Game Event Queue Demo")
    print("=" * 35)
    
    game_events = GameEventQueue()
    
    # Simulate game events
    events = [
        (EventType.MOVE, "Hero", None, {"position": "(5, 3)"}),
        (EventType.ATTACK, "Hero", "Goblin", {"damage": 15}),
        (EventType.DAMAGE, "Hero", None, {"damage": 8, "source": "Goblin"}),
        (EventType.HEAL, "Hero", None, {"amount": 25}),
        (EventType.COLLECT, "Hero", None, {"item": "Gold Coin"}),
        (EventType.ATTACK, "Hero", "Dragon", {"damage": 30}),
        (EventType.LEVEL_UP, "Hero", None, {"level": 2}),
        (EventType.COLLECT, "Hero", None, {"item": "Magic Sword"}),
    ]
    
    # Add all events
    print("📝 Adding game events:")
    for event_type, player, target, data in events:
        game_events.add_event(event_type, player, target, data)
    
    # Process all events
    print("\n🔄 Processing game events:")
    while game_events.event_queue:
        game_events.process_next_event()
    
    # Display final stats
    stats = game_events.get_stats()
    print(f"\n📊 Final Stats:")
    print(f"   Processed: {stats['processed']}")
    print(f"   Total Events: {stats['total']}")

game_event_demo()
```

---

## 📊 Performance Comparison

### ⏱️ Time Complexity Analysis

```python
"""
📊 Performance Comparison of Different Queue Implementations
Testing time complexity and efficiency
"""

import time
import sys
from collections import deque
import queue
import matplotlib.pyplot as plt
import random

def measure_time(func, *args):
    """Measure execution time of a function"""
    start = time.time()
    result = func(*args)
    end = time.time()
    return end - start, result

def test_list_queue(operations):
    """Test list-based queue performance"""
    q = []
    enqueue_times = []
    dequeue_times = []
    
    # Enqueue operations
    for i in range(operations):
        start = time.time()
        q.append(f"item_{i}")
        end = time.time()
        enqueue_times.append(end - start)
    
    # Dequeue operations
    for i in range(operations):
        start = time.time()
        q.pop(0)  # O(n) operation!
        end = time.time()
        dequeue_times.append(end - start)
    
    return enqueue_times, dequeue_times

def test_deque_queue(operations):
    """Test deque-based queue performance"""
    q = deque()
    enqueue_times = []
    dequeue_times = []
    
    # Enqueue operations
    for i in range(operations):
        start = time.time()
        q.append(f"item_{i}")
        end = time.time()
        enqueue_times.append(end - start)
    
    # Dequeue operations
    for i in range(operations):
        start = time.time()
        q.popleft()  # O(1) operation!
        end = time.time()
        dequeue_times.append(end - start)
    
    return enqueue_times, dequeue_times

def test_queue_module(operations):
    """Test queue.Queue performance"""
    q = queue.Queue()
    enqueue_times = []
    dequeue_times = []
    
    # Enqueue operations
    for i in range(operations):
        start = time.time()
        q.put(f"item_{i}")
        end = time.time()
        enqueue_times.append(end - start)
    
    # Dequeue operations
    for i in range(operations):
        start = time.time()
        q.get()
        end = time.time()
        dequeue_times.append(end - start)
    
    return enqueue_times, dequeue_times

def performance_comparison():
    """Run comprehensive performance comparison"""
    print("📊 Queue Performance Comparison")
    print("=" * 45)
    
    test_sizes = [100, 500, 1000, 2000]
    
    results = {
        'List Queue': {'enqueue': [], 'dequeue': [], 'total': []},
        'Deque Queue': {'enqueue': [], 'dequeue': [], 'total': []},
        'Queue Module': {'enqueue': [], 'dequeue': [], 'total': []}
    }
    
    for size in test_sizes:
        print(f"\n🧪 Testing with {size} operations:")
        
        # Test List Queue
        print("   📝 Testing List Queue...", end=" ")
        list_enq_times, list_deq_times = test_list_queue(size)
        list_total = sum(list_enq_times) + sum(list_deq_times)
        results['List Queue']['enqueue'].append(sum(list_enq_times))
        results['List Queue']['dequeue'].append(sum(list_deq_times))
        results['List Queue']['total'].append(list_total)
        print(f"Total: {list_total:.6f}s")
        
        # Test Deque Queue
        print("   🔄 Testing Deque Queue...", end=" ")
        deque_enq_times, deque_deq_times = test_deque_queue(size)
        deque_total = sum(deque_enq_times) + sum(deque_deq_times)
        results['Deque Queue']['enqueue'].append(sum(deque_enq_times))
        results['Deque Queue']['dequeue'].append(sum(deque_deq_times))
        results['Deque Queue']['total'].append(deque_total)
        print(f"Total: {deque_total:.6f}s")
        
        # Test Queue Module
        print("   🧵 Testing Queue Module...", end=" ")
        queue_enq_times, queue_deq_times = test_queue_module(size)
        queue_total = sum(queue_enq_times) + sum(queue_deq_times)
        results['Queue Module']['enqueue'].append(sum(queue_enq_times))
        results['Queue Module']['dequeue'].append(sum(queue_deq_times))
        results['Queue Module']['total'].append(queue_total)
        print(f"Total: {queue_total:.6f}s")
    
    # Display comparison table
    print("\n📈 Performance Summary:")
    print("=" * 60)
    print(f"{'Implementation':<15} {'100':<10} {'500':<10} {'1000':<10} {'2000':<10}")
    print("-" * 60)
    
    for impl_name, data in results.items():
        row = f"{impl_name:<15} "
        for i, size in enumerate(test_sizes):
            row += f"{data['total'][i]:.4f}s   "
        print(row)
    
    # Performance recommendations
    print("\n💡 Performance Recommendations:")
    print("=" * 40)
    print("🟢 collections.deque: Best for general queue operations")
    print("🟡 queue.Queue: Best for thread-safe operations")
    print("🔴 List: Avoid for large queues (O(n) dequeue)")
    
    return results

# Memory usage comparison
def memory_usage_test():
    """Test memory usage of different queue implementations"""
    print("\n💾 Memory Usage Comparison")
    print("=" * 35)
    
    size = 10000
    
    # Test List
    print("📝 Testing List memory usage...")
    list_queue = []
    for i in range(size):
        list_queue.append(f"item_{i}")
    list_size = sys.getsizeof(list_queue)
    print(f"   List Queue: {list_size} bytes")
    
    # Test Deque
    print("🔄 Testing Deque memory usage...")
    deque_queue = deque()
    for i in range(size):
        deque_queue.append(f"item_{i}")
    deque_size = sys.getsizeof(deque_queue)
    print(f"   Deque Queue: {deque_size} bytes")
    
    # Test Queue Module
    print("🧵 Testing Queue Module memory usage...")
    queue_obj = queue.Queue()
    for i in range(size):
        queue_obj.put(f"item_{i}")
    queue_size = sys.getsizeof(queue_obj.queue)
    print(f"   Queue Module: {queue_size} bytes")
    
    print(f"\n📊 Memory Efficiency Ranking:")
    print(f"   1. Deque: {deque_size} bytes")
    print(f"   2. List: {list_size} bytes")
    print(f"   3. Queue Module: {queue_size} bytes")

# Run performance tests
performance_comparison()
memory_usage_test()
```

### 📋 Comparison Table

| Feature | List Queue | collections.deque | queue.Queue | Custom Implementation |
|---------|------------|-------------------|-------------|----------------------|
| **Enqueue Time** | O(1) amortized | O(1) | O(1) | O(1) |
| **Dequeue Time** | O(n) | O(1) | O(1) | O(1) |
| **Memory Usage** | Medium | Low | Medium | Depends |
| **Thread Safety** | ❌ No | ❌ No | ✅ Yes | Depends |
| **Bounded Size** | ❌ No | ❌ No | ✅ Yes | Depends |
| **Best Use Case** | Small queues | General purpose | Multi-threading | Learning/Special needs |

---

## 🧪 Interactive Code Examples

### 🎯 Queue Visualizer

```python
"""
🎯 Interactive Queue Visualizer
Visual representation of queue operations
"""

class InteractiveQueueVisualizer:
    def __init__(self, max_display=10):
        self.queue = []
        self.max_display = max_display
        self.operation_count = 0
    
    def enqueue(self, item):
        """Add item with visual feedback"""
        self.queue.append(item)
        self.operation_count += 1
        
        print(f"\n🔥 ENQUEUE Operation #{self.operation_count}")
        print(f"   Adding: {item}")
        self._visualize_operation("ENQUEUE", item)
    
    def dequeue(self):
        """Remove item with visual feedback"""
        if not self.queue:
            print("\n❌ DEQUEUE Failed - Queue is empty!")
            return None
        
        item = self.queue.pop(0)
        self.operation_count += 1
        
        print(f"\n🔥 DEQUEUE Operation #{self.operation_count}")
        print(f"   Removing: {item}")
        self._visualize_operation("DEQUEUE", item)
        return item
    
    def peek(self):
        """View front item"""
        if not self.queue:
            print("\n👀 PEEK - Queue is empty!")
            return None
        
        front_item = self.queue[0]
        print(f"\n👀 PEEK Operation")
        print(f"   Front item: {front_item}")
        self._show_current_state()
        return front_item
    
    def _visualize_operation(self, operation, item):
        """Create visual representation of operation"""
        print(f"   📊 Queue state before {operation}:")
        
        if operation == "ENQUEUE":
            # Show adding to rear
            if len(self.queue) > 1:
                before_queue = self.queue[:-1]
                self._draw_queue(before_queue, highlight_rear=False)
            else:
                print("      [ EMPTY ]")
            
            print(f"   ➕ Adding '{item}' to REAR:")
            self._draw_queue(self.queue, highlight_rear=True)
        
        elif operation == "DEQUEUE":
            # Show removing from front
            before_queue = [item] + self.queue
            print(f"   ➖ Removing '{item}' from FRONT:")
            self._draw_queue(before_queue, highlight_front=True)
            
            print(f"   📊 Queue state after DEQUEUE:")
            if self.queue:
                self._draw_queue(self.queue)
            else:
                print("      [ EMPTY ]")
    
    def _draw_queue(self, items, highlight_front=False, highlight_rear=False):
        """Draw ASCII representation of queue"""
        if not items:
            print("      [ EMPTY ]")
            return
        
        # Limit display size
        display_items = items[:self.max_display]
        if len(items) > self.max_display:
            display_items.append("...")
        
        # Create top border
        border_width = sum(len(str(item)) + 3 for item in display_items) + 1
        print("      ┌" + "─" * (border_width - 2) + "┐")
        
        # Create item row
        item_row = "      │ "
        for i, item in enumerate(display_items):
            if highlight_front and i == 0:
                item_row += f"[{item}] "
            elif highlight_rear and i == len(display_items) - 1:
                item_row += f"[{item}] "
            else:
                item_row += f"{item} "
        item_row += "│"
        print(item_row)
        
        # Create bottom border
        print("      └" + "─" * (border_width - 2) + "┘")
        
        # Add pointers
        if len(display_items) > 1:
            if highlight_front:
                print("        ↑" + " " * (len(str(display_items[0])) + 2))
                print("      FRONT")
            elif highlight_rear:
                spaces = sum(len(str(item)) + 3 for item in display_items[:-1])
                print("      " + " " * spaces + "↑")
                print("      " + " " * spaces + "REAR")
            else:
                print("        ↑" + " " * (border_width - 10) + "↑")
                print("      FRONT" + " " * (border_width - 15) + "REAR")
    
    def _show_current_state(self):
        """Show current queue state"""
        print(f"   📊 Current queue state:")
        self._draw_queue(self.queue)
        print(f"   📏 Size: {len(self.queue)}")
    
    def interactive_demo(self):
        """Run interactive demonstration"""
        print("🎮 Interactive Queue Visualizer")
        print("=" * 40)
        print("Commands: enq <item>, deq, peek, quit")
        print("Example: enq Apple, deq, peek")
        print("-" * 40)
        
        while True:
            try:
                command = input("\n💻 Enter command: ").strip().lower()
                
                if command == 'quit' or command == 'exit':
                    print("👋 Thanks for using Queue Visualizer!")
                    break
                
                elif command.startswith('enq '):
                    item = command[4:].strip()
                    if item:
                        self.enqueue(item)
                    else:
                        print("❌ Please provide an item to enqueue")
                
                elif command == 'deq':
                    self.dequeue()
                
                elif command == 'peek':
                    self.peek()
                
                elif command == 'status':
                    self._show_current_state()
                
                elif command == 'help':
                    print("📖 Available commands:")
                    print("   enq <item> - Add item to queue")
                    print("   deq        - Remove item from queue")
                    print("   peek       - View front item")
                    print("   status     - Show queue state")
                    print("   quit       - Exit visualizer")
                
                else:
                    print("❌ Unknown command. Type 'help' for commands.")
                    
            except KeyboardInterrupt:
                print("\n👋 Exiting Queue Visualizer!")
                break
            except Exception as e:
                print(f"❌ Error: {e}")

# Auto-demo function
def auto_demo():
    """Automated demonstration"""
    print("🤖 Automated Queue Demo")
    print("=" * 30)
    
    visualizer = InteractiveQueueVisualizer()
    
    # Demonstrate various operations
    demo_operations = [
        ("enqueue", "🍎"),
        ("enqueue", "🍌"),
        ("enqueue", "🍊"),
        ("peek", None),
        ("dequeue", None),
        ("enqueue", "🥝"),
        ("enqueue", "🍇"),
        ("peek", None),
        ("dequeue", None),
        ("dequeue", None),
        ("dequeue", None),
        ("dequeue", None),  # This should fail
    ]
    
    for operation, item in demo_operations:
        input("\n⏸️ Press Enter to continue...")
        
        if operation == "enqueue":
            visualizer.enqueue(item)
        elif operation == "dequeue":
            visualizer.dequeue()
        elif operation == "peek":
            visualizer.peek()

# Uncomment to run interactive demo
# InteractiveQueueVisualizer().interactive_demo()

# Run automated demo
auto_demo()
```

---

## 🎮 Practice Challenges

### Challenge 1: 🏥 Hospital Queue Management

```python
"""
🏥 Challenge 1: Hospital Emergency Queue
Implement a priority-based patient queue system
"""

from dataclasses import dataclass
from typing import List
import heapq
from datetime import datetime

@dataclass
class Patient:
    name: str
    condition: str
    priority: int  # 1=Critical, 2=Urgent, 3=Standard
    arrival_time: datetime
    
    def __lt__(self, other):
        # Higher priority first, then earliest arrival
        if self.priority != other.priority:
            return self.priority < other.priority
        return self.arrival_time < other.arrival_time

class HospitalQueue:
    def __init__(self):
        self.queue = []
        self.treated_patients = []
    
    def admit_patient(self, name, condition, priority):
        """Add patient to queue"""
        patient = Patient(name, condition, priority, datetime.now())
        heapq.heappush(self.queue, patient)
        print(f"🏥 Patient admitted: {patient.name} - {patient.condition}")
        self._show_queue()
    
    def treat_next_patient(self):
        """Treat highest priority patient"""
        if not self.queue:
            print("✅ No patients waiting")
            return None
        
        patient = heapq.heappop(self.queue)
        self.treated_patients.append(patient)
        print(f"🩺 Treating: {patient.name} - {patient.condition}")
        self._show_queue()
        return patient
    
    def _show_queue(self):
        """Display current queue"""
        if not self.queue:
            print("📋 Emergency Queue: EMPTY")
            return
        
        print(f"📋 Emergency Queue ({len(self.queue)} patients):")
        for i, patient in enumerate(sorted(self.queue), 1):
            priority_emoji = ["🔴", "🟡", "🟢"][patient.priority - 1]
            print(f"   {i}. {priority_emoji} {patient.name} - {patient.condition}")

# Test the hospital queue
def hospital_challenge():
    print("🏥 Hospital Emergency Queue Challenge")
    print("=" * 45)
    
    hospital = HospitalQueue()
    
    # Add patients with different priorities
    patients = [
        ("John Smith", "Broken arm", 3),
        ("Emergency Patient", "Heart attack", 1),
        ("Jane Doe", "Severe bleeding", 2),
        ("Bob Wilson", "Minor cut", 3),
        ("Critical Case", "Stroke", 1),
        ("Mary Johnson", "High fever", 2)
    ]
    
    print("👥 Admitting patients:")
    for name, condition, priority in patients:
        hospital.admit_patient(name, condition, priority)
        print()
    
    print("🩺 Treating patients:")
    while hospital.queue:
        hospital.treat_next_patient()
        print()
    
    print(f"✅ All {len(hospital.treated_patients)} patients treated!")

hospital_challenge()
```

### Challenge 2: 🎫 Event Ticket Queue

```python
"""
🎫 Challenge 2: Concert Ticket Booking System
Handle multiple ticket counters with fair queuing
"""

from collections import deque
import threading
import time
import random

class Customer:
    def __init__(self, name, tickets_needed):
        self.name = name
        self.tickets_needed = tickets_needed
        self.wait_time = 0
        self.start_time = time.time()
    
    def __str__(self):
        return f"{self.name} (needs {self.tickets_needed} tickets)"

class TicketCounter:
    def __init__(self, counter_id, available_tickets=100):
        self.counter_id = counter_id
        self.queue = deque()
        self.available_tickets = available_tickets
        self.customers_served = 0
        self.is_open = True
    
    def add_customer(self, customer):
        """Add customer to counter queue"""
        self.queue.append(customer)
        print(f"🎫 Counter {self.counter_id}: {customer} joined queue (position {len(self.queue)})")
    
    def serve_customers(self):
        """Serve customers in queue"""
        while self.is_open and (self.queue or self.available_tickets > 0):
            if not self.queue:
                time.sleep(0.1)
                continue
            
            customer = self.queue.popleft()
            customer.wait_time = time.time() - customer.start_time
            
            # Simulate ticket processing time
            processing_time = random.uniform(1, 3)
            print(f"🎫 Counter {self.counter_id}: Serving {customer.name}...")
            time.sleep(processing_time)
            
            if self.available_tickets >= customer.tickets_needed:
                self.available_tickets -= customer.tickets_needed
                self.customers_served += 1
                print(f"✅ Counter {self.counter_id}: {customer.name} got {customer.tickets_needed} tickets!")
                print(f"   Wait time: {customer.wait_time:.1f}s, Remaining tickets: {self.available_tickets}")
            else:
                print(f"❌ Counter {self.counter_id}: Not enough tickets for {customer.name}")
            
            print(f"📊 Counter {self.counter_id}: {len(self.queue)} customers waiting")
    
    def close(self):
        """Close the counter"""
        self.is_open = False
        print(f"🚪 Counter {self.counter_id} closed")

class TicketingSystem:
    def __init__(self, num_counters=3):
        self.counters = [TicketCounter(i+1) for i in range(num_counters)]
        self.total_customers = 0
    
    def find_shortest_queue(self):
        """Find counter with shortest queue"""
        return min(self.counters, key=lambda c: len(c.queue))
    
    def add_customer(self, name, tickets_needed):
        """Add customer to shortest queue"""
        counter = self.find_shortest_queue()
        customer = Customer(name, tickets_needed)
        counter.add_customer(customer)
        self.total_customers += 1
    
    def start_serving(self):
        """Start serving customers at all counters"""
        threads = []
        for counter in self.counters:
            thread = threading.Thread(target=counter.serve_customers, daemon=True)
            thread.start()
            threads.append(thread)
        return threads
    
    def get_stats(self):
        """Get system statistics"""
        total_served = sum(c.customers_served for c in self.counters)
        total_tickets_sold = sum(100 - c.available_tickets for c in self.counters)
        return {
            'total_customers': self.total_customers,
            'customers_served': total_served,
            'tickets_sold': total_tickets_sold,
            'counters': len(self.counters)
        }

# Test the ticketing system
def ticketing_challenge():
    print("🎫 Concert Ticket Booking Challenge")
    print("=" * 40)
    
    system = TicketingSystem(num_counters=3)
    
    # Simulate customers arriving
    customers = [
        ("Alice", 2), ("Bob", 1), ("Charlie", 4),
        ("Diana", 3), ("Eve", 2), ("Frank", 1),
        ("Grace", 5), ("Henry", 2), ("Ivy", 3),
        ("Jack", 1), ("Kate", 4), ("Liam", 2)
    ]
    
    print("👥 Customers arriving:")
    for name, tickets in customers:
        system.add_customer(name, tickets)
    
    # Start serving
    print("\n🎫 Opening ticket counters...")
    threads = system.start_serving()
    
    # Wait for all customers to be served
    time.sleep(10)  # Simulate some processing time
    
    # Close counters
    for counter in system.counters:
        counter.close()
    
    # Wait for threads to finish
    for thread in threads:
        thread.join(timeout=1)
    
    # Display final statistics
    stats = system.get_stats()
    print(f"\n📊 Final Statistics:")
    print(f"   Total customers: {stats['total_customers']}")
    print(f"   Customers served: {stats['customers_served']}")
    print(f"   Tickets sold: {stats['tickets_sold']}")
    
    for i, counter in enumerate(system.counters):
        print(f"   Counter {i+1}: {counter.customers_served} served, {counter.available_tickets} tickets left")

ticketing_challenge()
```

### Challenge 3: 📚 Library Book Return System

```python
"""
📚 Challenge 3: Library Book Return and Processing System
Multi-queue system for different book processing stages
"""

from collections import deque
from enum import Enum
import time
import random

class BookStatus(Enum):
    RETURNED = "📥 Returned"
    CHECKED = "🔍 Quality Check"
    REPAIRED = "🔧 Repaired"
    SHELVED = "📚 Shelved"

class Book:
    def __init__(self, title, isbn, condition="good"):
        self.title = title
        self.isbn = isbn
        self.condition = condition  # good, damaged, lost
        self.status = BookStatus.RETURNED
        self.processing_time = time.time()
    
    def __str__(self):
        return f"{self.title} ({self.condition})"

class LibraryProcessingSystem:
    def __init__(self):
        self.return_queue = deque()          # Books just returned
        self.check_queue = deque()           # Books to be quality checked  
        self.repair_queue = deque()          # Books needing repair
        self.shelving_queue = deque()        # Books ready for shelving
        self.processed_books = []            # Completed books
        
        self.stats = {
            'returned': 0, 'checked': 0, 
            'repaired': 0, 'shelved': 0
        }
    
    def return_book(self, title, isbn, condition="good"):
        """Customer returns a book"""
        book = Book(title, isbn, condition)
        self.return_queue.append(book)
        self.stats['returned'] += 1
        
        print(f"📥 Book returned: {book}")
        self._display_queues()
    
    def process_returns(self):
        """Move books from return queue to check queue"""
        if not self.return_queue:
            return False
        
        book = self.return_queue.popleft()
        book.status = BookStatus.CHECKED
        self.check_queue.append(book)
        
        print(f"🔍 Quality checking: {book}")
        self._display_queues()
        return True
    
    def process_quality_check(self):
        """Check book quality and route accordingly"""
        if not self.check_queue:
            return False
        
        book = self.check_queue.popleft()
        self.stats['checked'] += 1
        
        # Simulate quality check
        if book.condition == "damaged":
            book.status = BookStatus.REPAIRED
            self.repair_queue.append(book)
            print(f"🔧 Book needs repair: {book}")
        else:
            book.status = BookStatus.SHELVED
            self.shelving_queue.append(book)
            print(f"📚 Book ready for shelving: {book}")
        
        self._display_queues()
        return True
    
    def process_repairs(self):
        """Process books in repair queue"""
        if not self.repair_queue:
            return False
        
        book = self.repair_queue.popleft()
        book.condition = "good"  # Book is now repaired
        book.status = BookStatus.SHELVED
        self.shelving_queue.append(book)
        self.stats['repaired'] += 1
        
        print(f"🔧 Book repaired and ready for shelving: {book}")
        self._display_queues()
        return True
    
    def process_shelving(self):
        """Shelve books from shelving queue"""
        if not self.shelving_queue:
            return False
        
        book = self.shelving_queue.popleft()
        self.processed_books.append(book)
        self.stats['shelved'] += 1
        
        total_time = time.time() - book.processing_time
        print(f"📚 Book shelved: {book} (processing time: {total_time:.1f}s)")
        self._display_queues()
        return True
    
    def _display_queues(self):
        """Display status of all queues"""
        print(f"📊 Queue Status:")
        print(f"   📥 Returns: {len(self.return_queue)}")
        print(f"   🔍 Quality Check: {len(self.check_queue)}")
        print(f"   🔧 Repairs: {len(self.repair_queue)}")
        print(f"   📚 Shelving: {len(self.shelving_queue)}")
        print(f"   ✅ Completed: {len(self.processed_books)}")
        print("-" * 40)
    
    def process_all_queues(self):
        """Process one item from each non-empty queue"""
        processed = False
        
        # Process in priority order
        if self.process_returns():
            processed = True
        if self.process_quality_check():
            processed = True
        if self.process_repairs():
            processed = True
        if self.process_shelving():
            processed = True
            
        return processed
    
    def get_final_stats(self):
        """Get processing statistics"""
        return {
            **self.stats,
            'total_processed': len(self.processed_books),
            'pending': (len(self.return_queue) + len(self.check_queue) + 
                       len(self.repair_queue) + len(self.shelving_queue))
        }

# Test the library system
def library_challenge():
    print("📚 Library Book Processing Challenge")
    print("=" * 45)
    
    library = LibraryProcessingSystem()
    
    # Books being returned
    returned_books = [
        ("Python Programming", "978-1234567890", "good"),
        ("Data Structures", "978-0987654321", "damaged"),
        ("Algorithms", "978-1122334455", "good"),
        ("Machine Learning", "978-5566778899", "good"),
        ("Database Systems", "978-9988776655", "damaged"),
        ("Web Development", "978-4433221100", "good"),
        ("Mobile Apps", "978-0011223344", "damaged"),
        ("Cloud Computing", "978-7788990011", "good"),
    ]
    
    print("📥 Books being returned:")
    for title, isbn, condition in returned_books:
        library.return_book(title, isbn, condition)
        time.sleep(0.1)  # Small delay between returns
    
    print("\n🔄 Processing all books through the system:")
    step = 1
    while library.process_all_queues():
        print(f"\n--- Processing Step {step} ---")
        step += 1
        time.sleep(0.2)  # Simulate processing time
    
    # Final statistics
    stats = library.get_final_stats()
    print(f"\n📊 Final Processing Statistics:")
    print(f"   Books returned: {stats['returned']}")
    print(f"   Books quality checked: {stats['checked']}")
    print(f"   Books repaired: {stats['repaired']}")
    print(f"   Books shelved: {stats['shelved']}")
    print(f"   Total processed: {stats['total_processed']}")
    print(f"   Pending books: {stats['pending']}")
    
    if stats['pending'] == 0:
        print("✅ All books successfully processed!")
    else:
        print("⚠️ Some books still pending processing")

library_challenge()
```

---

## 📚 Summary & Best Practices

### 🎯 Key Takeaways

1. **FIFO Principle**: Queues follow First-In, First-Out ordering
2. **Essential Operations**: Enqueue (add), Dequeue (remove), Peek (view front)
3. **Multiple Implementations**: Lists, deque, queue module, custom classes
4. **Performance Matters**: Choose implementation based on use case
5. **Real-World Applications**: Print spooling, web servers, game events, scheduling

### ✅ Best Practices

#### 🚀 Implementation Guidelines

```python
# ✅ DO: Use collections.deque for general-purpose queues
from collections import deque
queue = deque()
queue.append(item)      # O(1) enqueue
item = queue.popleft()  # O(1) dequeue

# ✅ DO: Use queue.Queue for thread-safe operations
import queue
thread_safe_queue = queue.Queue()

# ❌ DON'T: Use list.pop(0) for large queues
# This is O(n) and inefficient
queue = []
item = queue.pop(0)  # Avoid this!
```

#### 🎯 Choosing the Right Queue

| Use Case | Recommended Implementation | Reason |
|----------|---------------------------|---------|
| **General Purpose** | `collections.deque` | O(1) operations, memory efficient |
| **Multi-threading** | `queue.Queue` | Thread-safe, blocking operations |
| **Priority-based** | `heapq` with custom class | Efficient priority handling |
| **Bounded Size** | `queue.Queue(maxsize=n)` | Built-in size limits |
| **Learning/Custom** | Custom implementation | Full control and understanding |

#### 💡 Design Patterns

```python
# ✅ DO: Handle empty queue gracefully
def safe_dequeue(queue):
    if not queue:
        return None
    return queue.popleft()

# ✅ DO: Add queue size monitoring
class MonitoredQueue:
    def __init__(self, max_size=None):
        self.queue = deque()
        self.max_size = max_size
    
    def enqueue(self, item):
        if self.max_size and len(self.queue) >= self.max_size:
            raise Exception("Queue is full")
        self.queue.append(item)

# ✅ DO: Use context managers for queue operations
from contextlib import contextmanager

@contextmanager
def queue_operation(queue):
    try:
        yield queue
    except Exception as e:
        print(f"Queue operation failed: {e}")
        raise
```

#### 🔒 Thread Safety Considerations

```python
# ✅ Thread-safe queue operations
import threading
import queue

def producer(q):
    for i in range(5):
        q.put(f"item_{i}")

def consumer(q):
    while True:
        try:
            item = q.get(timeout=1)
            print(f"Processed: {item}")
            q.task_done()
        except queue.Empty:
            break

# Safe multi-threading with queue.Queue
job_queue = queue.Queue()
producer_thread = threading.Thread(target=producer, args=(job_queue,))
consumer_thread = threading.Thread(target=consumer, args=(job_queue,))
```

### 🚨 Common Pitfalls to Avoid

1. **Using `list.pop(0)`** for large queues (O(n) complexity)
2. **Not handling empty queues** (leads to exceptions)
3. **Ignoring thread safety** in concurrent applications
4. **Not considering memory usage** for long-running queues
5. **Missing queue size limits** (can cause memory issues)

### 📈 Performance Optimization Tips

```python
# ✅ Batch operations when possible
def batch_enqueue(queue, items):
    for item in items:
        queue.append(item)

# ✅ Use appropriate data structures
# For small queues (< 100 items): list is OK
# For large queues: always use deque
# For thread-safe: use queue.Queue

# ✅ Monitor queue sizes
def monitor_queue_health(queue, name, max_size=1000):
    size = len(queue)
    if size > max_size:
        print(f"⚠️ Warning: {name} queue size ({size}) exceeds threshold")
```

### 🎓 Further Learning Resources

- **Real Python**: Advanced queue patterns and async queues
- **Python Documentation**: `collections.deque` and `queue` modules  
- **Algorithm Textbooks**: Queue applications in graph traversal
- **System Design**: Message queues and distributed systems
- **Concurrent Programming**: Producer-consumer patterns

### 🏆 Congratulations!

You've mastered Python queues! You now understand:
- ✅ Queue fundamentals and FIFO principles
- ✅ Multiple implementation approaches
- ✅ Performance characteristics and trade-offs
- ✅ Real-world applications and use cases
- ✅ Best practices and common pitfalls
- ✅ Advanced queue types and patterns

**Keep practicing** with the interactive examples and challenges to solidify your understanding! 🚀

---

*Happy Coding! 🐍✨*