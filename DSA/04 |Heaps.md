# 🌟 Python Heaps: The Ultimate Interactive Guide 🐍

> *Master the art of efficient priority queues and heap operations in Python with visual representations and hands-on examples!*

[![Python Heaps](https://img.shields.io/badge/Python-Heaps-blue?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
![Topic](https://img.shields.io/badge/Topic-Data%20Structures-green?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-Beginner%20to%20Advanced-orange?style=for-the-badge)

---

## 📋 Table of Contents
1. [🔥 Introduction to Heaps](#-introduction-to-heaps)
2. [🎯 Heap Fundamentals](#-heap-fundamentals)
3. [🐍 Python heapq Module](#-python-heapq-module)
4. [🛠️ Core Operations](#️-core-operations)
5. [💡 Visual Representations](#-visual-representations)
6. [🚀 Practical Examples](#-practical-examples)
7. [⚡ Advanced Techniques](#-advanced-techniques)
8. [🎪 Real-World Applications](#-real-world-applications)
9. [📚 Best Practices](#-best-practices)
10. [🧪 Exercises & Challenges](#-exercises--challenges)

---

## 🔥 Introduction to Heaps

Welcome to the fascinating world of **Python Heaps**! 🎉 

A **heap** is a specialized tree-based data structure that maintains a specific ordering property, making it perfect for implementing **priority queues**. Think of it as a VIP queue where the most important elements always get served first!

### 🎯 Why Heaps Matter

```python
# Without heaps: Finding minimum in unsorted list - O(n)
def find_min_slow(lst):
    return min(lst)  # Scans entire list

# With heaps: Finding minimum - O(1)
import heapq
heap = [1, 3, 5, 7, 8, 6, 9]
heapq.heapify(heap)
minimum = heap[0]  # Instant access!
```

---

## 🎯 Heap Fundamentals

### 🌳 Heap Properties

A heap is a **complete binary tree** with special ordering:

#### 🔹 Min-Heap Property
> Parent ≤ Children (smallest element at root)

#### 🔸 Max-Heap Property  
> Parent ≥ Children (largest element at root)

### 📊 Visual Representation

```
           MIN HEAP                    MAX HEAP
              1                          12
            /   \                      /    \
           3     5                   10      9
          / \   / \                 / \    / \
         7   8 6   9               8   7  6   5
        /\                        /\
       10 12                     3  1

    Array: [1,3,5,7,8,6,9,10,12]   Array: [12,10,9,8,7,6,5,3,1]
```

### 🔢 Array Indexing Magic

```
For element at index i:
├── Parent:      (i-1) // 2
├── Left Child:  2*i + 1  
└── Right Child: 2*i + 2

Example with index 2 (value 5):
├── Parent:      (2-1)//2 = 0 → value 1
├── Left Child:  2*2+1 = 5 → value 6
└── Right Child: 2*2+2 = 6 → value 9
```

---

## 🐍 Python heapq Module

Python's `heapq` module provides a **min-heap** implementation using regular lists!

### 📥 Import & Setup

```python
import heapq

# Create empty heap
heap = []

# Or convert existing list
numbers = [4, 1, 7, 3, 8, 5]
heapq.heapify(numbers)  # Transform to heap in-place
print(numbers)  # [1, 3, 5, 4, 8, 7]
```

### 🎨 Module Functions Overview

```
┌─────────────────────────────────────────────────────────────┐
│                    HEAPQ MODULE FUNCTIONS                   │
├─────────────────┬───────────────────────────────────────────┤
│ heapify(list)   │ Convert list to heap - O(n)              │
│ heappush(h, x)  │ Add element to heap - O(log n)           │
│ heappop(heap)   │ Remove & return smallest - O(log n)      │
│ heappushpop()   │ Push then pop - O(log n)                 │
│ heapreplace()   │ Pop then push - O(log n)                 │
│ nlargest(k, h)  │ Get k largest elements - O(k log n)      │
│ nsmallest(k, h) │ Get k smallest elements - O(k log n)     │
└─────────────────┴───────────────────────────────────────────┘
```

---

## 🛠️ Core Operations

### 1. 🏗️ Creating a Heap

#### Method 1: Start Empty
```python
import heapq

# Empty heap
heap = []

# Add elements one by one
heapq.heappush(heap, 10)
heapq.heappush(heap, 5)
heapq.heappush(heap, 20)
heapq.heappush(heap, 1)

print(heap)  # [1, 5, 20, 10]
```

#### Method 2: Convert Existing List
```python
# Start with unsorted list
data = [20, 1, 5, 12, 9, 8, 15]

# Convert to heap
heapq.heapify(data)
print(data)  # [1, 9, 5, 12, 20, 8, 15]
```

### 2. ➕ Adding Elements (heappush)

```python
heap = [1, 3, 5, 7, 8, 6, 9]

# Add new element
heapq.heappush(heap, 2)

# Heap automatically maintains order
print(heap)  # [1, 2, 5, 3, 8, 6, 9, 7]

# Visual representation:
#       1
#     /   \
#    2     5
#   / \   / \
#  3   8 6   9
# /
#7
```

### 3. ➖ Removing Elements (heappop)

```python
heap = [1, 3, 5, 7, 8, 6, 9]

# Remove and return smallest element
smallest = heapq.heappop(heap)
print(f"Removed: {smallest}")  # Removed: 1
print(f"Heap: {heap}")         # [3, 7, 5, 9, 8, 6]

# Always removes root (minimum) element!
```

### 4. 👀 Peeking at Root

```python
heap = [1, 3, 5, 7, 8, 6, 9]

# Access minimum without removing
minimum = heap[0]  # O(1) operation!
print(f"Minimum: {minimum}")  # Minimum: 1
```

---

## 💡 Visual Representations

### 🎨 ASCII Art Examples

#### Min-Heap Structure
```
                     1                    ← Root (minimum)
                   /   \
                  3     5                 ← Level 1
                 / \   / \
                7   8 6   9               ← Level 2
               / \
              10 12                       ← Level 3 (partial)

Array Representation: [1, 3, 5, 7, 8, 6, 9, 10, 12]
Indices:               0  1  2  3  4  5  6   7   8
```

#### Heap Operation Flow
```
📥 INSERTION PROCESS 📥

Step 1: Add to end        Step 2: Bubble up       Step 3: Final heap
       1                         1                       1
     /   \                     /   \                   /   \
    3     5         →         3     5        →        2     5
   / \   /                   / \   / \               / \   /
  7   8 6                   7   8 6   2             3   8 6
                               ↑
                        Violates heap property!
```

#### Priority Queue Visualization
```
🎯 PRIORITY QUEUE OPERATIONS 🎯

High Priority │ (1, "🚨 Emergency")  │ ← heappop() gets this first
              │ (2, "⚠️  Urgent")    │
              │ (3, "📋 Normal")     │
              │ (4, "⏰ Scheduled")  │
Low Priority  │ (5, "💤 Low")       │ ← heappop() gets this last
```

---

## 🚀 Practical Examples

### 🏥 Example 1: Hospital Emergency System

```python
import heapq

class EmergencySystem:
    def __init__(self):
        self.patients = []
        self.patient_id = 0
    
    def add_patient(self, name, severity, condition):
        """Add patient with priority based on severity (1=critical, 5=minor)"""
        patient = (severity, self.patient_id, name, condition)
        heapq.heappush(self.patients, patient)
        self.patient_id += 1
        print(f"✅ Added: {name} (Priority: {severity}) - {condition}")
    
    def treat_next(self):
        """Treat highest priority patient"""
        if not self.patients:
            print("🏥 No patients waiting")
            return None
        
        severity, _, name, condition = heapq.heappop(self.patients)
        print(f"🚑 Now treating: {name} (Priority: {severity}) - {condition}")
        return name
    
    def show_queue(self):
        """Display current queue"""
        print("\n📋 Current Queue:")
        for i, (severity, _, name, condition) in enumerate(self.patients):
            print(f"   {i+1}. {name} - Priority: {severity} - {condition}")

# Demo
hospital = EmergencySystem()

# Add patients
hospital.add_patient("Alice", 1, "Heart Attack")
hospital.add_patient("Bob", 3, "Broken Arm")
hospital.add_patient("Charlie", 2, "Severe Bleeding")
hospital.add_patient("Diana", 1, "Stroke")

hospital.show_queue()

# Treat patients in priority order
print("\n🏥 Treatment Order:")
while hospital.patients:
    hospital.treat_next()
```

**Output:**
```
✅ Added: Alice (Priority: 1) - Heart Attack
✅ Added: Bob (Priority: 3) - Broken Arm
✅ Added: Charlie (Priority: 2) - Severe Bleeding
✅ Added: Diana (Priority: 1) - Stroke

📋 Current Queue:
   1. Alice - Priority: 1 - Heart Attack
   2. Diana - Priority: 1 - Stroke
   3. Bob - Priority: 3 - Broken Arm
   4. Charlie - Priority: 2 - Severe Bleeding

🏥 Treatment Order:
🚑 Now treating: Alice (Priority: 1) - Heart Attack
🚑 Now treating: Diana (Priority: 1) - Stroke
🚑 Now treating: Charlie (Priority: 2) - Severe Bleeding
🚑 Now treating: Bob (Priority: 3) - Broken Arm
```

### 🎮 Example 2: Game Task Scheduler

```python
import heapq
import time

class TaskScheduler:
    def __init__(self):
        self.tasks = []
        
    def schedule_task(self, delay, priority, task_name, function):
        """Schedule a task to run after delay seconds with given priority"""
        run_time = time.time() + delay
        task = (run_time, priority, task_name, function)
        heapq.heappush(self.tasks, task)
        print(f"📅 Scheduled: {task_name} (Priority: {priority}) in {delay}s")
    
    def process_tasks(self):
        """Process all ready tasks in priority order"""
        current_time = time.time()
        processed = []
        
        while self.tasks:
            run_time, priority, name, func = self.tasks[0]
            
            if run_time <= current_time:
                # Task is ready to run
                heapq.heappop(self.tasks)
                print(f"🎯 Executing: {name} (Priority: {priority})")
                try:
                    func()
                    processed.append(name)
                except Exception as e:
                    print(f"❌ Error in {name}: {e}")
            else:
                # No more ready tasks
                break
        
        return processed

# Demo functions
def spawn_enemy():
    print("   👾 Enemy spawned!")

def collect_powerup():
    print("   ⭐ Power-up collected!")

def save_game():
    print("   💾 Game saved!")

def update_leaderboard():
    print("   🏆 Leaderboard updated!")

# Demo
scheduler = TaskScheduler()

# Schedule tasks (delay, priority, name, function)
scheduler.schedule_task(0, 1, "Spawn Boss", spawn_enemy)
scheduler.schedule_task(0, 3, "Collect Coin", collect_powerup)
scheduler.schedule_task(0, 2, "Auto-save", save_game)
scheduler.schedule_task(0, 1, "Update Score", update_leaderboard)

print("\n⏰ Processing tasks...")
scheduler.process_tasks()
```

### 📊 Example 3: Top K Elements Finder

```python
import heapq

class TopKFinder:
    def __init__(self, k):
        self.k = k
        self.heap = []
    
    def add_number(self, num):
        """Add number and maintain top K largest elements"""
        if len(self.heap) < self.k:
            heapq.heappush(self.heap, num)
        elif num > self.heap[0]:  # num is larger than smallest in top K
            heapq.heapreplace(self.heap, num)
        
        return self.get_kth_largest()
    
    def get_kth_largest(self):
        """Get the Kth largest element"""
        return self.heap[0] if self.heap else None
    
    def get_top_k(self):
        """Get all top K elements (sorted)"""
        return sorted(self.heap, reverse=True)

# Demo: Finding top 3 largest numbers in a stream
finder = TopKFinder(k=3)

numbers = [4, 5, 8, 2, 3, 7, 1, 9, 6]

print("📊 Finding Top 3 Largest Numbers in Stream:")
print("─" * 50)

for num in numbers:
    kth_largest = finder.add_number(num)
    top_k = finder.get_top_k()
    print(f"Added {num} → 3rd largest: {kth_largest}, Top 3: {top_k}")
```

**Output:**
```
📊 Finding Top 3 Largest Numbers in Stream:
──────────────────────────────────────────────────
Added 4 → 3rd largest: 4, Top 3: [4]
Added 5 → 3rd largest: 4, Top 3: [5, 4]
Added 8 → 3rd largest: 4, Top 3: [8, 5, 4]
Added 2 → 3rd largest: 4, Top 3: [8, 5, 4]
Added 3 → 3rd largest: 4, Top 3: [8, 5, 4]
Added 7 → 3rd largest: 5, Top 3: [8, 7, 5]
Added 1 → 3rd largest: 5, Top 3: [8, 7, 5]
Added 9 → 3rd largest: 7, Top 3: [9, 8, 7]
Added 6 → 3rd largest: 7, Top 3: [9, 8, 7]
```

---

## ⚡ Advanced Techniques

### 🔄 Creating Max-Heap with Min-Heap

Since Python's `heapq` only provides min-heap, here's how to simulate max-heap:

```python
import heapq

class MaxHeap:
    def __init__(self):
        self.heap = []
    
    def push(self, val):
        """Add element to max heap"""
        heapq.heappush(self.heap, -val)  # Negate for max behavior
    
    def pop(self):
        """Remove and return maximum element"""
        if self.heap:
            return -heapq.heappop(self.heap)  # Negate back
        return None
    
    def peek(self):
        """Get maximum without removing"""
        if self.heap:
            return -self.heap[0]
        return None
    
    def __str__(self):
        # Show actual values (not negated)
        return str([-x for x in self.heap])

# Demo
max_heap = MaxHeap()

# Add elements
for val in [3, 1, 6, 5, 2, 4]:
    max_heap.push(val)
    print(f"Added {val}: {max_heap}")

print("\n🔥 Popping maximum elements:")
while max_heap.heap:
    maximum = max_heap.pop()
    print(f"Popped: {maximum}, Remaining: {max_heap}")
```

### 🔗 Heap with Custom Objects

```python
import heapq
from dataclasses import dataclass, field
from typing import Any

@dataclass
class Task:
    priority: int
    name: str
    description: str
    created_at: float = field(default_factory=time.time)
    
    def __lt__(self, other):
        """Define comparison for heap ordering"""
        # Lower priority number = higher priority
        if self.priority != other.priority:
            return self.priority < other.priority
        # If same priority, earlier creation time wins
        return self.created_at < other.created_at

class SmartTaskQueue:
    def __init__(self):
        self.tasks = []
        
    def add_task(self, priority, name, description):
        """Add task to queue"""
        task = Task(priority, name, description)
        heapq.heappush(self.tasks, task)
        print(f"📝 Added: {name} (P{priority})")
    
    def get_next_task(self):
        """Get highest priority task"""
        if self.tasks:
            task = heapq.heappop(self.tasks)
            print(f"🎯 Processing: {task.name} (P{task.priority})")
            return task
        return None
    
    def show_queue(self):
        """Show current queue"""
        print("\n📋 Task Queue:")
        for i, task in enumerate(self.tasks):
            print(f"   {i+1}. {task.name} (P{task.priority}) - {task.description}")

# Demo
import time

queue = SmartTaskQueue()

# Add tasks with different priorities
queue.add_task(1, "Fix Critical Bug", "Server is down!")
queue.add_task(3, "Write Documentation", "Update API docs")
queue.add_task(1, "Security Patch", "Apply urgent security fix")
queue.add_task(2, "Code Review", "Review pull request #123")

queue.show_queue()

print("\n⚡ Processing tasks by priority:")
while queue.tasks:
    queue.get_next_task()
```

---

## 🎪 Real-World Applications

### 1. 🌐 Dijkstra's Algorithm (Shortest Path)

```python
import heapq
from collections import defaultdict, deque

class Graph:
    def __init__(self):
        self.graph = defaultdict(list)
    
    def add_edge(self, u, v, weight):
        """Add weighted edge to graph"""
        self.graph[u].append((v, weight))
        self.graph[v].append((u, weight))  # Undirected graph
    
    def dijkstra(self, start, end):
        """Find shortest path using heap-based priority queue"""
        # Distance dictionary
        distances = defaultdict(lambda: float('inf'))
        distances[start] = 0
        
        # Previous node tracking for path reconstruction
        previous = {}
        
        # Priority queue: (distance, node)
        pq = [(0, start)]
        visited = set()
        
        while pq:
            current_dist, current_node = heapq.heappop(pq)
            
            if current_node in visited:
                continue
                
            visited.add(current_node)
            
            # Found destination
            if current_node == end:
                break
            
            # Check neighbors
            for neighbor, weight in self.graph[current_node]:
                if neighbor not in visited:
                    new_dist = current_dist + weight
                    
                    if new_dist < distances[neighbor]:
                        distances[neighbor] = new_dist
                        previous[neighbor] = current_node
                        heapq.heappush(pq, (new_dist, neighbor))
        
        # Reconstruct path
        path = []
        current = end
        while current in previous:
            path.append(current)
            current = previous[current]
        path.append(start)
        path.reverse()
        
        return distances[end], path

# Demo: City Navigation System
print("🗺️  City Navigation System")
print("=" * 40)

city = Graph()

# Add roads with distances (in km)
city.add_edge("Home", "Mall", 5)
city.add_edge("Home", "Park", 3)
city.add_edge("Mall", "Airport", 8)
city.add_edge("Park", "Airport", 12)
city.add_edge("Park", "Hospital", 4)
city.add_edge("Hospital", "Airport", 6)

# Find shortest route
start, destination = "Home", "Airport"
distance, path = city.dijkstra(start, destination)

print(f"🚗 Shortest route from {start} to {destination}:")
print(f"   Path: {' → '.join(path)}")
print(f"   Distance: {distance} km")
```

### 2. 🎵 Music Streaming Recommendation Engine

```python
import heapq
from collections import namedtuple
import random

Song = namedtuple('Song', ['id', 'title', 'artist', 'genre', 'rating'])

class MusicRecommendationEngine:
    def __init__(self, max_recommendations=10):
        self.max_recommendations = max_recommendations
        self.user_preferences = {}
        self.songs_heap = []
        
    def add_user_preference(self, genre, weight):
        """Add or update user preference for a genre"""
        self.user_preferences[genre] = weight
    
    def calculate_song_score(self, song):
        """Calculate recommendation score for a song"""
        base_score = song.rating
        genre_bonus = self.user_preferences.get(song.genre, 0) * 2
        return base_score + genre_bonus
    
    def add_song_candidate(self, song):
        """Add song as recommendation candidate"""
        score = self.calculate_song_score(song)
        
        # Use negative score for max-heap behavior
        if len(self.songs_heap) < self.max_recommendations:
            heapq.heappush(self.songs_heap, (-score, song.id, song))
        else:
            # Replace if this song has higher score than lowest
            if score > -self.songs_heap[0][0]:
                heapq.heapreplace(self.songs_heap, (-score, song.id, song))
    
    def get_recommendations(self):
        """Get top recommended songs"""
        # Sort by score (descending)
        recommendations = sorted(self.songs_heap, key=lambda x: x[0])
        return [(song, -score) for score, _, song in recommendations]

# Demo: Personal Music Recommender
print("🎵 Personal Music Recommendation Engine")
print("=" * 45)

recommender = MusicRecommendationEngine(max_recommendations=5)

# Set user preferences (genre weights)
recommender.add_user_preference("Rock", 5)
recommender.add_user_preference("Pop", 3)
recommender.add_user_preference("Jazz", 4)

# Sample songs database
songs_db = [
    Song(1, "Bohemian Rhapsody", "Queen", "Rock", 9.5),
    Song(2, "Shape of You", "Ed Sheeran", "Pop", 8.2),
    Song(3, "Take Five", "Dave Brubeck", "Jazz", 9.0),
    Song(4, "Hotel California", "Eagles", "Rock", 9.3),
    Song(5, "Billie Jean", "Michael Jackson", "Pop", 8.8),
    Song(6, "Kind of Blue", "Miles Davis", "Jazz", 9.4),
    Song(7, "Imagine", "John Lennon", "Pop", 8.5),
    Song(8, "Stairway to Heaven", "Led Zeppelin", "Rock", 9.7),
    Song(9, "Blue in Green", "Bill Evans", "Jazz", 8.9),
    Song(10, "Sweet Child O' Mine", "Guns N' Roses", "Rock", 8.7),
]

# Add all songs as candidates
for song in songs_db:
    recommender.add_song_candidate(song)

# Get and display recommendations
recommendations = recommender.get_recommendations()

print("🎯 Your Top Recommendations:")
print("-" * 30)
for i, (song, score) in enumerate(recommendations, 1):
    print(f"{i}. {song.title} by {song.artist}")
    print(f"   Genre: {song.genre} | Rating: {song.rating} | Score: {score:.1f}")
    print()
```

---

## 📚 Best Practices

### ✅ DO's

1. **Use heapq for Priority Queues**
   ```python
   # ✅ Good: Use heapq for efficient priority operations
   import heapq
   tasks = []
   heapq.heappush(tasks, (priority, task_id, data))
   ```

2. **Leverage Tuples for Complex Priorities**
   ```python
   # ✅ Good: Multi-level priority sorting
   heapq.heappush(heap, (primary_priority, secondary_priority, data))
   ```

3. **Use heapify() for Bulk Operations**
   ```python
   # ✅ Good: Convert existing list efficiently
   data = [5, 2, 8, 1, 9]
   heapq.heapify(data)  # O(n) time
   ```

### ❌ DON'Ts

1. **Don't Manually Sort for Priority Operations**
   ```python
   # ❌ Bad: Sorting entire list repeatedly
   def get_min_priority_task(tasks):
       return min(tasks, key=lambda x: x.priority)
   
   # ✅ Good: Use heap
   min_task = heapq.heappop(task_heap)
   ```

2. **Don't Modify Heap Directly**
   ```python
   # ❌ Bad: Breaking heap property
   heap[0] = new_value  # Violates heap invariant
   
   # ✅ Good: Use proper heap operations
   heapq.heappop(heap)
   heapq.heappush(heap, new_value)
   ```

### 🎯 Performance Tips

```python
# Performance Comparison
import time
import heapq
import random

def compare_approaches(n=10000):
    """Compare heap vs list operations"""
    data = [random.randint(1, 1000) for _ in range(n)]
    
    # Method 1: Using heap
    start = time.time()
    heap_data = data.copy()
    heapq.heapify(heap_data)
    
    for _ in range(100):
        heapq.heappop(heap_data)
        heapq.heappush(heap_data, random.randint(1, 1000))
    
    heap_time = time.time() - start
    
    # Method 2: Using sorted list
    start = time.time()
    list_data = sorted(data)
    
    for _ in range(100):
        list_data.pop(0)  # Remove minimum
        list_data.append(random.randint(1, 1000))
        list_data.sort()  # Re-sort
    
    list_time = time.time() - start
    
    print(f"📊 Performance Comparison (n={n}):")
    print(f"   Heap approach: {heap_time:.4f} seconds")
    print(f"   List approach: {list_time:.4f} seconds")
    print(f"   Heap is {list_time/heap_time:.1f}x faster!")

compare_approaches()
```

---

## 🧪 Exercises & Challenges

### 🎯 Beginner Challenges

#### Challenge 1: Merge K Sorted Lists
```python
def merge_k_sorted_lists(lists):
    """
    Merge k sorted lists using a heap.
    
    Example:
    Input: [[1,4,5], [1,3,4], [2,6]]
    Output: [1,1,2,3,4,4,5,6]
    """
    import heapq
    
    # Your solution here
    heap = []
    result = []
    
    # Initialize heap with first element from each list
    # Process and merge
    # Return merged result
    
    pass

# Test your solution
test_lists = [[1,4,5], [1,3,4], [2,6]]
print("🎯 Challenge 1 Result:")
print(merge_k_sorted_lists(test_lists))
```

#### Challenge 2: Find Median in Data Stream
```python
class MedianFinder:
    """
    Find median of numbers in a data stream.
    Use two heaps: max_heap for smaller half, min_heap for larger half
    """
    
    def __init__(self):
        # Your initialization here
        pass
    
    def add_number(self, num):
        """Add number to data stream"""
        # Your solution here
        pass
    
    def find_median(self):
        """Return current median"""
        # Your solution here
        pass

# Test your solution
median_finder = MedianFinder()
numbers = [5, 15, 1, 3]

print("🎯 Challenge 2 - Streaming Median:")
for num in numbers:
    median_finder.add_number(num)
    print(f"Added {num} → Median: {median_finder.find_median()}")
```

### 🔥 Intermediate Challenges

#### Challenge 3: Task Scheduler with Dependencies
```python
class TaskSchedulerWithDependencies:
    """
    Schedule tasks with dependencies using topological sort + heap
    """
    
    def __init__(self):
        self.tasks = {}
        self.dependencies = {}
        self.in_degree = {}
    
    def add_task(self, task_id, priority, duration):
        """Add task with priority and duration"""
        # Your implementation
        pass
    
    def add_dependency(self, task_a, task_b):
        """task_a must complete before task_b can start"""
        # Your implementation
        pass
    
    def get_execution_order(self):
        """Return optimal execution order considering dependencies and priorities"""
        # Your implementation using heap + topological sort
        pass

# Test your solution
scheduler = TaskSchedulerWithDependencies()

# Add tasks (id, priority, duration)
scheduler.add_task("A", 1, 5)
scheduler.add_task("B", 2, 3)
scheduler.add_task("C", 1, 4)
scheduler.add_task("D", 3, 2)

# Add dependencies
scheduler.add_dependency("A", "C")  # A must finish before C
scheduler.add_dependency("B", "D")  # B must finish before D

print("🎯 Challenge 3 - Task Execution Order:")
print(scheduler.get_execution_order())
```

### 💯 Solutions & Hints

#### Solution 1: Merge K Sorted Lists
```python
def merge_k_sorted_lists_solution(lists):
    """Complete solution with explanation"""
    import heapq
    
    heap = []
    result = []
    
    # Initialize heap with first element from each non-empty list
    for i, lst in enumerate(lists):
        if lst:
            heapq.heappush(heap, (lst[0], i, 0))  # (value, list_index, element_index)
    
    while heap:
        val, list_idx, elem_idx = heapq.heappop(heap)
        result.append(val)
        
        # Add next element from the same list if available
        if elem_idx + 1 < len(lists[list_idx]):
            next_val = lists[list_idx][elem_idx + 1]
            heapq.heappush(heap, (next_val, list_idx, elem_idx + 1))
    
    return result

# Test
test_lists = [[1,4,5], [1,3,4], [2,6]]
print("✅ Solution 1:", merge_k_sorted_lists_solution(test_lists))
```

---

## 🎊 Conclusion

Congratulations! 🎉 You've mastered Python heaps! Here's what you've learned:

### 🏆 Key Takeaways

- ✅ **Heaps** are perfect for priority queues and finding min/max elements efficiently
- ✅ **Python's heapq** module provides optimized min-heap operations
- ✅ **O(log n)** insertion and deletion make heaps highly efficient
- ✅ **Real-world applications** include task scheduling, pathfinding, and recommendation systems
- ✅ **Best practices** ensure optimal performance and maintainable code

### 🚀 Next Steps

1. **Practice** with more LeetCode heap problems
2. **Implement** heap-based solutions in your projects
3. **Explore** advanced heap variants (Fibonacci heaps, Binary heaps)
4. **Build** a complete priority queue system

### 📖 Additional Resources

- 📚 [Python heapq Documentation](https://docs.python.org/3/library/heapq.html)
- 🎓 [Algorithms Course - Heaps](https://www.coursera.org/learn/algorithms-part1)
- 💻 [LeetCode Heap Problems](https://leetcode.com/tag/heap/)
- 📱 [Visualizing Algorithms](https://visualgo.net/en/heap)

---

## 🎨 ASCII Art Gallery

```
    🏆 HEAP MASTERY ACHIEVED! 🏆
    
         .-..-. 
        /  ||  \  
       |   ||   |
        \  ||  /
         '-''-' 
    
    📚 Knowledge Level: EXPERT 📚
    🎯 Skills Unlocked: ALL 🎯
    
    ╔══════════════════════════════╗
    ║  🐍 Python Heap Ninja 🐍    ║
    ║                              ║
    ║  ✓ Min/Max Heap Operations   ║
    ║  ✓ Priority Queue Design     ║  
    ║  ✓ Algorithm Optimization    ║
    ║  ✓ Real-world Applications   ║
    ╚══════════════════════════════╝
    
    Ready to heap big success! 🚀
```

---

*Happy Coding! 🐍✨*