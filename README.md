# Java DSA Cheat Sheet

## I. Basic Syntax & Concepts

* **Main Method:**
    ```java
    public class MyClass {
        public static void main(String[] args) {
            // Your code here
        }
    }
    ```
* **Variable Declaration:**
    ```java
    int num = 10;
    String text = "hello";
    boolean isTrue = true;
    double price = 19.99;
    char grade = 'A';
    ```
* **Input (Scanner):**
    ```java
    import java.util.Scanner;
    Scanner sc = new Scanner(System.in);
    int inputInt = sc.nextInt();
    String inputString = sc.next(); // single word
    String inputLine = sc.nextLine(); // full line
    sc.close(); // Important!
    ```
* **Output:**
    ```java
    System.out.println("Hello World"); // with newline
    System.out.print("Hello"); // without newline
    System.out.printf("Value: %d, Text: %s%n", num, text); // formatted output
    ```
* **Arrays:**
    ```java
    int[] arr = new int[5]; // Declares an array of size 5
    int[] initializedArr = {1, 2, 3, 4, 5};
    arr[0] = 10; // Accessing/assigning
    int len = arr.length; // Length of array
    ```
* **Loops:**
    ```java
    // For loop
    for (int i = 0; i < arr.length; i++) {
        // ...
    }
    // Enhanced for loop (for-each)
    for (int val : arr) {
        // ...
    }
    // While loop
    int i = 0;
    while (i < 5) {
        // ...
        i++;
    }
    ```
* **Conditional Statements:**
    ```java
    if (condition) {
        // ...
    } else if (anotherCondition) {
        // ...
    } else {
        // ...
    }
    ```
* **Functions/Methods:**
    ```java
    public static int add(int a, int b) {
        return a + b;
    }
    ```

## II. Essential Data Structures (Java Collections Framework)

**Always `import java.util.*;` or specifically import the classes you need.**

### 1. List (Ordered, allows duplicates, index-based)

* **`ArrayList<E>` (Dynamic Array):**
    * **Declaration:** `List<Integer> list = new ArrayList<>();`
    * **Add:** `list.add(element);` (to end), `list.add(index, element);`
    * **Get:** `list.get(index);`
    * **Set:** `list.set(index, newElement);`
    * **Remove:** `list.remove(index);` or `list.remove(Object element);`
    * **Size:** `list.size();`
    * **Contains:** `list.contains(element);`
    * **Iteration:**
        ```java
        for (int i = 0; i < list.size(); i++) {
            // list.get(i)
        }
        for (Integer val : list) {
            // val
        }
        ```
    * **Time Complexities:** Access/Get: $O(1)$; Add (amortized to end): $O(1)$; Add/Remove (middle): $O(N)$
* **`LinkedList<E>` (Doubly Linked List):**
    * **Declaration:** `List<String> linkedList = new LinkedList<>();`
    * **Common methods (same as ArrayList):** `add()`, `get()`, `remove()`, `size()`, `contains()`.
    * **Specific methods (often $O(1)$ at ends):** `addFirst()`, `addLast()`, `removeFirst()`, `removeLast()`, `getFirst()`, `getLast()`.
    * **Time Complexities:** Add/Remove (ends): $O(1)$; Add/Remove (middle): $O(N)$; Access/Get: $O(N)$

### 2. Set (Unordered, unique elements)

* **`HashSet<E>` (Hash Table based):**
    * **Declaration:** `Set<String> set = new HashSet<>();`
    * **Add:** `set.add(element);`
    * **Remove:** `set.remove(element);`
    * **Contains:** `set.contains(element);`
    * **Size:** `set.size();`
    * **Time Complexities:** Add, Remove, Contains: Average $O(1)$, Worst $O(N)$
* **`TreeSet<E>` (Red-Black Tree based, sorted order):**
    * **Declaration:** `Set<Integer> sortedSet = new TreeSet<>();`
    * **Add, Remove, Contains:** $O(\log N)$
    * **Additional methods:** `first()`, `last()`, `floor()`, `ceiling()`, `lower()`, `higher()`.

### 3. Map (Key-Value pairs, unique keys)

* **`HashMap<K, V>` (Hash Table based):**
    * **Declaration:** `Map<String, Integer> map = new HashMap<>();`
    * **Put:** `map.put(key, value);`
    * **Get:** `map.get(key);` (returns `null` if key not found)
    * **Remove:** `map.remove(key);`
    * **Contains Key:** `map.containsKey(key);`
    * **Contains Value:** `map.containsValue(value);`
    * **Size:** `map.size();`
    * **Iterate Keys:** `for (String key : map.keySet()) { ... }`
    * **Iterate Values:** `for (Integer value : map.values()) { ... }`
    * **Iterate Entries:**
        ```java
        for (Map.Entry<String, Integer> entry : map.entrySet()) {
            String key = entry.getKey();
            Integer value = entry.getValue();
        }
        ```
    * **Time Complexities:** Put, Get, Remove, ContainsKey: Average $O(1)$, Worst $O(N)$
* **`TreeMap<K, V>` (Red-Black Tree based, sorted by keys):**
    * **Declaration:** `Map<Integer, String> sortedMap = new TreeMap<>();`
    * **Put, Get, Remove, ContainsKey:** $O(\log N)$
    * **Additional methods:** `firstKey()`, `lastKey()`, `floorKey()`, `ceilingKey()`.

### 4. Queue (FIFO - First-In, First-Out)

* **`Queue<E>` (Interface, typically implemented by `LinkedList` or `ArrayDeque`):**
    * **Declaration:** `Queue<Integer> queue = new LinkedList<>();`
    * **Add:** `queue.offer(element);` (returns `false` if full, use `add()` for exception)
    * **Remove:** `queue.poll();` (returns `null` if empty, use `remove()` for exception)
    * **Peek:** `queue.peek();` (returns `null` if empty, use `element()` for exception)
    * **Size:** `queue.size();`
    * **Time Complexities:** All operations: $O(1)$

### 5. Deque (Double-Ended Queue, can add/remove from both ends)

* **`Deque<E>` (Interface, typically implemented by `ArrayDeque` or `LinkedList`):**
    * **Declaration:** `Deque<Character> deque = new ArrayDeque<>();`
    * **Add:** `addFirst()`, `addLast()`, `offerFirst()`, `offerLast()`
    * **Remove:** `removeFirst()`, `removeLast()`, `pollFirst()`, `pollLast()`
    * **Peek:** `peekFirst()`, `peekLast()`
    * **Time Complexities:** All operations: $O(1)$
    * **Can be used as a Stack:** `push()`, `pop()`, `peek()` (all $O(1)$)

### 6. Stack (LIFO - Last-In, First-Out)

* **`Stack<E>` (Legacy class, extends `Vector`):**
    * **Declaration:** `Stack<Double> stack = new Stack<>();`
    * **Add:** `stack.push(element);`
    * **Remove:** `stack.pop();`
    * **Peek:** `stack.peek();`
    * **Empty:** `stack.empty();`
    * **Time Complexities:** All operations: $O(1)$
    * **Note:** For modern Java, `Deque<E> deque = new ArrayDeque<>();` is generally preferred when you need Stack-like behavior.

### 7. PriorityQueue (Heap - min-heap by default)

* **`PriorityQueue<E>` (Min-heap by default):**
    * **Declaration (Min-heap):** `PriorityQueue<Integer> pq = new PriorityQueue<>();`
    * **Declaration (Max-heap):** `PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());`
    * **Declaration (Custom Comparator):**
        ```java
        // For pairs or custom objects, e.g., sort by second element descending
        PriorityQueue<int[]> customPQ = new PriorityQueue<>((a, b) -> b[1] - a[1]);
        ```
    * **Add:** `pq.offer(element);` (or `add()`)
    * **Remove (min/max element):** `pq.poll();`
    * **Peek (min/max element):** `pq.peek();`
    * **Size:** `pq.size();`
    * **Time Complexities:** Add, Remove, Peek: $O(\log N)$

## III. Utility Classes & Important Methods

* **`Arrays` (for arrays of primitives/Objects):**
    * **Sorting:** `Arrays.sort(arr);` ($O(N \log N)$)
    * **Binary Search:** `Arrays.binarySearch(arr, key);` ($O(\log N)$, array must be sorted)
    * **Fill:** `Arrays.fill(arr, value);`
    * **Copy:** `Arrays.copyOf(arr, newLength);`
    * **Convert to List:** `Arrays.asList(T... a);` (returns a fixed-size list, not `ArrayList`)
* **`Collections` (for Collection objects like List, Set, Queue):**
    * **Sorting List:** `Collections.sort(list);` ($O(N \log N)$)
    * **Reverse List:** `Collections.reverse(list);`
    * **Frequency:** `Collections.frequency(collection, element);`
    * **Min/Max:** `Collections.min(collection);`, `Collections.max(collection);`
* **`String` Methods:**
    * `length()`: Length of string.
    * `charAt(index)`: Character at index.
    * `substring(startIndex, endIndex)`: Substring (endIndex exclusive).
    * `indexOf(char/String)`: First occurrence.
    * `lastIndexOf(char/String)`: Last occurrence.
    * `startsWith()`, `endsWith()`, `contains()`.
    * `equals()`, `equalsIgnoreCase()`.
    * `toLowerCase()`, `toUpperCase()`.
    * `toCharArray()`: Convert to char array.
    * `split(regex)`: Split string into array.
    * `trim()`: Remove leading/trailing whitespace.
    * **`StringBuilder` (for mutable strings/efficient concatenation):**
        * `StringBuilder sb = new StringBuilder();`
        * `sb.append(data);`
        * `sb.toString();`
        * `sb.reverse();`

## IV. Custom Classes (Nodes for Trees/Linked Lists)

```java
// For Linked Lists
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) { this.val = val; }
    ListNode(int val, ListNode next) { this.val = val; this.next = next; }
}

// For Binary Trees
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int val) { this.val = val; }
    TreeNode(int val, TreeNode left, TreeNode right) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}
