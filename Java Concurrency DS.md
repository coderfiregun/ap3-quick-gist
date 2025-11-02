# Java Concurrency Collections Cheatsheet 🚀

## 📋 Quick Reference Table

| Collection | Thread-Safe? | Blocking? | Ordering | Nulls? | Best Use Case |
|------------|--------------|-----------|----------|--------|---------------|
| `ConcurrentHashMap` | ✅ | ❌ | None | ❌ | General caching, counters |
| `CopyOnWriteArrayList` | ✅ | ❌ | Insertion | ✅ | Read-heavy lists, listeners |
| `ConcurrentLinkedQueue` | ✅ | ❌ | FIFO | ❌ | Lock-free queue |
| `LinkedBlockingQueue` | ✅ | ✅ | FIFO | ❌ | Producer-consumer (bounded) |
| `ArrayBlockingQueue` | ✅ | ✅ | FIFO | ❌ | Fixed-size buffer |
| `PriorityBlockingQueue` | ✅ | ✅ | Priority | ❌ | Task scheduling |
| `SynchronousQueue` | ✅ | ✅ | N/A | ❌ | Direct handoff |
| `DelayQueue` | ✅ | ✅ | Delay | ❌ | Scheduled tasks |
| `ConcurrentSkipListMap` | ✅ | ❌ | Sorted | ❌ | Sorted concurrent map |
| `ConcurrentSkipListSet` | ✅ | ❌ | Sorted | ❌ | Sorted concurrent set |
| `ConcurrentLinkedDeque` | ✅ | ❌ | FIFO/LIFO | ❌ | Work stealing |

---

## 1️⃣ ConcurrentHashMap ⭐⭐⭐

**When to Use:** General-purpose concurrent map, caching, counters

```java
// Basic operations - thread-safe!
ConcurrentHashMap<Integer, String> map = new ConcurrentHashMap<>();
map.put(1, "value");
String value = map.get(1);
map.remove(1);

// Atomic operations (better than get-then-put)
map.putIfAbsent(1, "value");
map.computeIfAbsent(1, k -> expensiveComputation(k));
map.computeIfPresent(1, (k, v) -> v + "_updated");
map.merge(1, "new", (old, new) -> old + new);

// Atomic counter
map.compute(key, (k, v) -> v == null ? 1 : v + 1);
```

**Real Example: Request Counter**
```java
class RequestCounter {
    private ConcurrentHashMap<String, AtomicLong> counts = new ConcurrentHashMap<>();
    
    public void increment(String endpoint) {
        counts.computeIfAbsent(endpoint, k -> new AtomicLong()).incrementAndGet();
    }
    
    public long getCount(String endpoint) {
        return counts.getOrDefault(endpoint, new AtomicLong()).get();
    }
}
```

**Performance:**
- Read: O(1), highly concurrent
- Write: O(1), segment-locked
- Better than `Collections.synchronizedMap()`

---

## 2️⃣ BlockingQueue - Producer-Consumer Pattern ⭐⭐⭐

### **LinkedBlockingQueue** (Most Common)

```java
BlockingQueue<Task> queue = new LinkedBlockingQueue<>(100); // bounded

// Producer
queue.put(task);              // Blocks if full
queue.offer(task);            // Returns false if full
queue.offer(task, 1, SECONDS); // Waits with timeout

// Consumer
Task task = queue.take();            // Blocks if empty
Task task = queue.poll();            // Returns null if empty
Task task = queue.poll(1, SECONDS);  // Waits with timeout
```

### **Complete Producer-Consumer Example**

```java
class ProducerConsumerExample {
    private static final int CAPACITY = 10;
    private BlockingQueue<Integer> queue = new LinkedBlockingQueue<>(CAPACITY);
    
    // Producer thread
    class Producer implements Runnable {
        public void run() {
            try {
                for (int i = 0; i < 100; i++) {
                    queue.put(i);  // Blocks if queue is full
                    System.out.println("Produced: " + i);
                    Thread.sleep(100);
                }
                queue.put(-1); // Poison pill to signal end
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
        }
    }
    
    // Consumer thread
    class Consumer implements Runnable {
        public void run() {
            try {
                while (true) {
                    Integer item = queue.take();  // Blocks if queue is empty
                    if (item == -1) break;  // Poison pill
                    System.out.println("Consumed: " + item);
                    Thread.sleep(200);
                }
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
        }
    }
    
    public void start() {
        new Thread(new Producer()).start();
        new Thread(new Consumer()).start();
        new Thread(new Consumer()).start(); // Multiple consumers
    }
}
```

### **ArrayBlockingQueue** (Fixed Size)

```java
BlockingQueue<Task> queue = new ArrayBlockingQueue<>(100);
// Fixed capacity, array-backed
// Use when you want bounded memory
```

### **PriorityBlockingQueue** (Ordered by Priority)

```java
class Task implements Comparable<Task> {
    int priority;
    String name;
    
    public int compareTo(Task other) {
        return Integer.compare(this.priority, other.priority);
    }
}

BlockingQueue<Task> queue = new PriorityBlockingQueue<>();
// Higher priority tasks come out first
// Unbounded (grows as needed)
```

### **SynchronousQueue** (Direct Handoff)

```java
BlockingQueue<Task> queue = new SynchronousQueue<>();
// No capacity - producer waits for consumer
// Used in Executors.newCachedThreadPool()

// Producer blocks until consumer takes
queue.put(task);

// Consumer blocks until producer puts
Task task = queue.take();
```

---

## 3️⃣ Producer-Consumer Patterns & Solutions 🎯

### **Pattern 1: Single Producer, Single Consumer**

```java
BlockingQueue<Item> queue = new LinkedBlockingQueue<>(100);

// Producer
new Thread(() -> {
    while (producing) {
        Item item = produce();
        queue.put(item);
    }
}).start();

// Consumer
new Thread(() -> {
    while (consuming) {
        Item item = queue.take();
        process(item);
    }
}).start();
```

### **Pattern 2: Multiple Producers, Multiple Consumers**

```java
class TaskProcessor {
    private BlockingQueue<Task> queue = new LinkedBlockingQueue<>(1000);
    private ExecutorService producers = Executors.newFixedThreadPool(5);
    private ExecutorService consumers = Executors.newFixedThreadPool(10);
    
    public void start() {
        // Start producers
        for (int i = 0; i < 5; i++) {
            producers.submit(() -> {
                while (true) {
                    Task task = generateTask();
                    queue.put(task);
                }
            });
        }
        
        // Start consumers
        for (int i = 0; i < 10; i++) {
            consumers.submit(() -> {
                while (true) {
                    Task task = queue.take();
                    processTask(task);
                }
            });
        }
    }
}
```

### **Pattern 3: Graceful Shutdown (Poison Pill)**

```java
class GracefulShutdown {
    private BlockingQueue<Task> queue = new LinkedBlockingQueue<>();
    private static final Task POISON_PILL = new Task(-1, "STOP");
    
    class Producer implements Runnable {
        public void run() {
            try {
                while (hasWork()) {
                    queue.put(createTask());
                }
                queue.put(POISON_PILL); // Signal end
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
        }
    }
    
    class Consumer implements Runnable {
        public void run() {
            try {
                while (true) {
                    Task task = queue.take();
                    if (task == POISON_PILL) {
                        queue.put(POISON_PILL); // For other consumers
                        break;
                    }
                    process(task);
                }
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
        }
    }
}
```

### **Pattern 4: Rate Limiting**

```java
class RateLimitedProcessor {
    private BlockingQueue<Request> queue = new LinkedBlockingQueue<>(1000);
    private ScheduledExecutorService scheduler = Executors.newScheduledThreadPool(1);
    
    public void start() {
        // Process at most 100 requests per second
        scheduler.scheduleAtFixedRate(() -> {
            try {
                for (int i = 0; i < 100; i++) {
                    Request req = queue.poll();
                    if (req != null) {
                        process(req);
                    }
                }
            } catch (Exception e) {
                // Handle error
            }
        }, 0, 1, TimeUnit.SECONDS);
    }
    
    public void submit(Request req) throws InterruptedException {
        queue.put(req);
    }
}
```

### **Pattern 5: Work Stealing (Fork-Join)**

```java
class WorkStealingExample {
    private ConcurrentLinkedDeque<Task> deque = new ConcurrentLinkedDeque<>();
    
    // Worker adds tasks to own queue
    public void addTask(Task task) {
        deque.addLast(task); // Add to end
    }
    
    // Worker takes from own queue
    public Task takeTask() {
        return deque.pollLast(); // Take from end (LIFO)
    }
    
    // Other workers steal from this queue
    public Task stealTask() {
        return deque.pollFirst(); // Steal from front (FIFO)
    }
}
```

---

## 4️⃣ CopyOnWriteArrayList

**When to Use:** Read-heavy, rare writes (event listeners, observers)

```java
List<EventListener> listeners = new CopyOnWriteArrayList<>();

// Thread-safe adds (expensive - copies entire array)
listeners.add(newListener);

// Thread-safe iteration (snapshot - never throws ConcurrentModificationException)
for (EventListener listener : listeners) {
    listener.onEvent(event); // Safe even if another thread modifies
}
```

**Real Example: Event Notification**
```java
class EventBus {
    private CopyOnWriteArrayList<EventListener> listeners = new CopyOnWriteArrayList<>();
    
    public void register(EventListener listener) {
        listeners.add(listener);
    }
    
    public void fireEvent(Event event) {
        for (EventListener listener : listeners) {
            listener.onEvent(event);
        }
    }
}
```

**Performance:**
- Read: O(1), no locking
- Write: O(n), full array copy
- Iteration: Never throws ConcurrentModificationException

---

## 5️⃣ ConcurrentLinkedQueue

**When to Use:** Lock-free FIFO queue, high throughput

```java
Queue<Task> queue = new ConcurrentLinkedQueue<>();

// All thread-safe, non-blocking
queue.offer(task);  // Add to tail
Task task = queue.poll();   // Remove from head
Task peek = queue.peek();   // View head without removing
```

**Real Example: Event Processing**
```java
class EventProcessor {
    private ConcurrentLinkedQueue<Event> events = new ConcurrentLinkedQueue<>();
    
    public void addEvent(Event event) {
        events.offer(event);
    }
    
    public void processEvents() {
        Event event;
        while ((event = events.poll()) != null) {
            handle(event);
        }
    }
}
```

**vs BlockingQueue:**
- ✅ Lock-free, higher throughput
- ❌ No blocking (poll returns null if empty)
- ❌ Unbounded (can grow indefinitely)

---

## 6️⃣ Atomic Classes

**When to Use:** Single variables, counters, flags

```java
// Counters
AtomicInteger counter = new AtomicInteger(0);
counter.incrementAndGet();      // Atomic ++counter
counter.getAndIncrement();      // Atomic counter++
counter.addAndGet(5);           // Atomic counter += 5
counter.compareAndSet(5, 10);   // CAS: if value==5, set to 10

// Flags
AtomicBoolean flag = new AtomicBoolean(false);
flag.compareAndSet(false, true); // Atomic flip

// References
AtomicReference<Node> head = new AtomicReference<>();
head.compareAndSet(oldHead, newHead);

// Arrays
AtomicIntegerArray arr = new AtomicIntegerArray(10);
arr.incrementAndGet(0); // Atomic increment at index 0
```

**Real Example: Hit Counter**
```java
class HitCounter {
    private AtomicLong hits = new AtomicLong(0);
    private AtomicLong misses = new AtomicLong(0);
    
    public void recordHit() {
        hits.incrementAndGet();
    }
    
    public void recordMiss() {
        misses.incrementAndGet();
    }
    
    public double getHitRate() {
        long h = hits.get();
        long m = misses.get();
        return h / (double)(h + m);
    }
}
```

---

## 7️⃣ ConcurrentSkipListMap/Set

**When to Use:** Need sorted keys with concurrent access

```java
ConcurrentNavigableMap<Integer, String> map = new ConcurrentSkipListMap<>();

// Thread-safe sorted operations
map.put(5, "five");
map.put(1, "one");
map.put(10, "ten");

map.firstKey();           // 1
map.lastKey();            // 10
map.subMap(2, 8);         // {5="five"}
map.headMap(5);           // {1="one"}
map.tailMap(5);           // {5="five", 10="ten"}

// Set version
ConcurrentSkipListSet<Integer> set = new ConcurrentSkipListSet<>();
```

**Performance:** O(log n) for all operations

---

## 8️⃣ Comparison: Old vs New

### ❌ DON'T USE (Old, Slower)
```java
Map<K, V> map = Collections.synchronizedMap(new HashMap<>());
List<E> list = Collections.synchronizedList(new ArrayList<>());
Set<E> set = Collections.synchronizedSet(new HashSet<>());

// Problems:
// - Entire collection locked for every operation
// - Iteration requires manual synchronization
// - Poor concurrent performance
```

### ✅ USE INSTEAD (Modern, Faster)
```java
Map<K, V> map = new ConcurrentHashMap<>();
List<E> list = new CopyOnWriteArrayList<>();
Set<E> set = ConcurrentHashMap.newKeySet();

// Benefits:
// - Finer-grained locking
// - Better concurrent performance
// - Safe iteration without locks
```

---

## 🎯 Decision Tree: Which Collection?

```
Need a Map?
├─ Sorted keys? → ConcurrentSkipListMap
└─ Not sorted? → ConcurrentHashMap

Need a Set?
├─ Sorted? → ConcurrentSkipListSet
└─ Not sorted? → ConcurrentHashMap.newKeySet()

Need a List?
├─ Read-heavy? → CopyOnWriteArrayList
└─ Write-heavy? → Use ArrayList + ReentrantReadWriteLock

Need a Queue?
├─ Need blocking? (Producer-Consumer)
│  ├─ Bounded? → LinkedBlockingQueue / ArrayBlockingQueue
│  ├─ Priority? → PriorityBlockingQueue
│  ├─ Direct handoff? → SynchronousQueue
│  └─ Delayed? → DelayQueue
└─ Non-blocking? → ConcurrentLinkedQueue

Need a Deque?
└─ ConcurrentLinkedDeque (work stealing)

Need single variable?
└─ AtomicInteger / AtomicLong / AtomicBoolean / AtomicReference
```

---

## 🔥 Common Interview Patterns

### **Pattern: Thread-Safe Singleton**
```java
class Singleton {
    private static final AtomicReference<Singleton> instance = new AtomicReference<>();
    
    public static Singleton getInstance() {
        Singleton current = instance.get();
        if (current == null) {
            current = new Singleton();
            if (!instance.compareAndSet(null, current)) {
                current = instance.get();
            }
        }
        return current;
    }
}
```

### **Pattern: Thread-Safe Cache with Expiration**
```java
class ExpiringCache {
    private ConcurrentHashMap<String, CacheEntry> cache = new ConcurrentHashMap<>();
    private DelayQueue<CacheEntry> expiryQueue = new DelayQueue<>();
    
    public void put(String key, String value, long ttlMillis) {
        CacheEntry entry = new CacheEntry(key, value, ttlMillis);
        cache.put(key, entry);
        expiryQueue.put(entry);
    }
    
    public String get(String key) {
        CacheEntry entry = cache.get(key);
        return (entry != null && !entry.isExpired()) ? entry.value : null;
    }
    
    // Background cleanup thread
    public void startCleanup() {
        new Thread(() -> {
            while (true) {
                CacheEntry expired = expiryQueue.take();
                cache.remove(expired.key);
            }
        }).start();
    }
}
```

### **Pattern: Distributed Task Processing**
```java
class DistributedTaskProcessor {
    private LinkedBlockingQueue<Task> pendingTasks = new LinkedBlockingQueue<>(1000);
    private ConcurrentHashMap<String, TaskResult> results = new ConcurrentHashMap<>();
    private ExecutorService workers = Executors.newFixedThreadPool(10);
    
    public String submitTask(Task task) {
        String taskId = UUID.randomUUID().toString();
        task.setId(taskId);
        pendingTasks.offer(task);
        return taskId;
    }
    
    public TaskResult getResult(String taskId) {
        return results.get(taskId);
    }
    
    public void start() {
        for (int i = 0; i < 10; i++) {
            workers.submit(() -> {
                while (true) {
                    Task task = pendingTasks.take();
                    TaskResult result = process(task);
                    results.put(task.getId(), result);
                }
            });
        }
    }
}
```

---

## 💡 Key Takeaways

1. **ConcurrentHashMap** - Your go-to for maps (95% of cases)
2. **BlockingQueue** - Producer-consumer patterns
3. **CopyOnWriteArrayList** - Event listeners, observers
4. **AtomicXxx** - Simple counters and flags
5. **ConcurrentLinkedQueue** - Lock-free, high-throughput queues

**Never use:** `Collections.synchronizedXxx()` in new code!

**Always remember:**
- BlockingQueue for producer-consumer
- ConcurrentHashMap for caching
- Atomic classes for counters
- Let Java handle the synchronization! 🎯