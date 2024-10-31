## **1. Set Interface**
The **Set Interface** in Java is part of the **Java Collection Framework** and represents a collection of unique elements, meaning no duplicates are allowed. The `Set` interface extends the `Collection` interface and provides methods that manage unique collections of objects.

### Key Characteristics of Set:
- **No Duplicates**: A set does not allow duplicate elements.
- **Unordered Collection**: Sets generally do not maintain any specific order of elements (although some implementations, like `LinkedHashSet`, do maintain insertion order).
- **Implements Collection Interface**: Set inherits methods from the Collection interface, such as `add`, `remove`, `size`, `contains`, etc.

### Main Implementations of Set Interface:

1. **HashSet**
   - Stores elements in a hash table.
   - Does not maintain any order of elements.
   - Fast access and retrieval due to hashing.
   
   ```java
   import java.util.HashSet;
   import java.util.Set;

   public class HashSetExample {
       public static void main(String[] args) {
           Set<String> set = new HashSet<>();
           set.add("Apple");
           set.add("Banana");
           set.add("Orange");
           set.add("Apple");  // Duplicate, will not be added

           System.out.println(set); // Output may be in any order
       }
   }
   ```

2. **LinkedHashSet**
   - Maintains the insertion order of elements.
   - Good for cases where you need unique elements and order of insertion matters.
   
   ```java
   import java.util.LinkedHashSet;
   import java.util.Set;

   public class LinkedHashSetExample {
       public static void main(String[] args) {
           Set<String> set = new LinkedHashSet<>();
           set.add("Apple");
           set.add("Banana");
           set.add("Orange");

           System.out.println(set); // Output: [Apple, Banana, Orange]
       }
   }
   ```

3. **TreeSet**
   - Stores elements in a **sorted order** (natural ordering or by a comparator).
   - Based on a **Red-Black tree** (a self-balancing binary search tree).
   - Slower than `HashSet` for basic operations but maintains order.

   ```java
   import java.util.Set;
   import java.util.TreeSet;

   public class TreeSetExample {
       public static void main(String[] args) {
           Set<String> set = new TreeSet<>();
           set.add("Banana");
           set.add("Apple");
           set.add("Orange");

           System.out.println(set); // Output: [Apple, Banana, Orange] in sorted order
       }
   }
   ```

### Important Methods of the Set Interface
| Method                | Description |
|-----------------------|-------------|
| `add(E e)`            | Adds the specified element if it is not already present. |
| `remove(Object o)`    | Removes the specified element if present. |
| `contains(Object o)`  | Returns `true` if the set contains the specified element. |
| `size()`              | Returns the number of elements in the set. |
| `isEmpty()`           | Returns `true` if the set is empty. |
| `clear()`             | Removes all elements from the set. |

### Use Cases for Set
- **Storing Unique Data**: Useful for cases where duplicate data is not allowed, like a list of student IDs, emails, etc.
- **Removing Duplicates**: A `Set` can be used to remove duplicate elements from a collection.
- **Membership Testing**: Fast membership tests are possible with `HashSet` due to hashing.

### Example of Set Operations in Java

```java
import java.util.HashSet;
import java.util.Set;

public class SetOperationsExample {
    public static void main(String[] args) {
        Set<Integer> setA = new HashSet<>();
        setA.add(1);
        setA.add(2);
        setA.add(3);

        Set<Integer> setB = new HashSet<>();
        setB.add(3);
        setB.add(4);
        setB.add(5);

        // Union
        Set<Integer> union = new HashSet<>(setA);
        union.addAll(setB);
        System.out.println("Union: " + union); // Output: [1, 2, 3, 4, 5]

        // Intersection
        Set<Integer> intersection = new HashSet<>(setA);
        intersection.retainAll(setB);
        System.out.println("Intersection: " + intersection); // Output: [3]

        // Difference
        Set<Integer> difference = new HashSet<>(setA);
        difference.removeAll(setB);
        System.out.println("Difference: " + difference); // Output: [1, 2]
    }
}
```

### Summary
- `Set` is a collection that contains no duplicate elements.
- Implementations like `HashSet`, `LinkedHashSet`, and `TreeSet` offer different ways of managing sets.
- Each implementation serves different needs depending on order requirements and sorting.
  
Understanding these will help in choosing the right `Set` implementation for specific scenarios in Java.
<br> 
<br> 
<br> 
## **2. SortedSet**
The **SortedSet** interface in Java is part of the **Java Collection Framework** and extends the **Set** interface. It represents a set of unique elements, just like a regular set, but with one key difference: the elements in a `SortedSet` are sorted in ascending order.

### Key Characteristics of `SortedSet`:
- **Maintains Sorted Order**: Elements are automatically stored in ascending order (natural ordering or based on a custom comparator).
- **No Duplicates**: Like any `Set`, `SortedSet` does not allow duplicate elements.
- **Navigable**: It provides additional methods to navigate through elements in a sorted manner.

### Main Implementations of `SortedSet`
The primary implementation of `SortedSet` in Java is the **TreeSet** class, which maintains sorted order based on natural ordering or a provided `Comparator`.

### Key Methods of `SortedSet`
| Method               | Description |
|----------------------|-------------|
| `first()`            | Returns the first (lowest) element in the set. |
| `last()`             | Returns the last (highest) element in the set. |
| `headSet(E toElement)` | Returns a view of the portion of this set whose elements are strictly less than `toElement`. |
| `tailSet(E fromElement)` | Returns a view of the portion of this set whose elements are greater than or equal to `fromElement`. |
| `subSet(E fromElement, E toElement)` | Returns a view of the portion of this set within a range (`fromElement`, inclusive; `toElement`, exclusive). |
| `comparator()`       | Returns the comparator used to order the elements, or `null` if the natural ordering is used. |

### Example of Using `SortedSet` with `TreeSet`

Here's an example that demonstrates the basic usage of `SortedSet`:

```java
import java.util.SortedSet;
import java.util.TreeSet;

public class SortedSetExample {
    public static void main(String[] args) {
        // Creating a SortedSet of Integer type
        SortedSet<Integer> sortedSet = new TreeSet<>();

        // Adding elements to the SortedSet
        sortedSet.add(5);
        sortedSet.add(2);
        sortedSet.add(10);
        sortedSet.add(1);

        // Elements will be in sorted order
        System.out.println("SortedSet: " + sortedSet); // Output: [1, 2, 5, 10]

        // Accessing the first and last elements
        System.out.println("First element: " + sortedSet.first()); // Output: 1
        System.out.println("Last element: " + sortedSet.last());   // Output: 10

        // Getting a subset
        SortedSet<Integer> headSet = sortedSet.headSet(5);
        System.out.println("HeadSet less than 5: " + headSet); // Output: [1, 2]

        SortedSet<Integer> tailSet = sortedSet.tailSet(5);
        System.out.println("TailSet from 5: " + tailSet);      // Output: [5, 10]

        SortedSet<Integer> subSet = sortedSet.subSet(2, 10);
        System.out.println("SubSet from 2 to 10: " + subSet);  // Output: [2, 5]
    }
}
```

### Explanation of Example Code:
- **Sorting and Duplicate-Free**: `TreeSet` automatically sorts the integers and does not allow duplicates.
- **Accessing Elements**: `first()` and `last()` provide quick access to the smallest and largest elements.
- **Range Views**: `headSet`, `tailSet`, and `subSet` create views of specific ranges of elements within the `SortedSet`.

### Real-World Use Cases
- **Sorted Unique Data**: Useful for any scenario requiring a sorted list of unique elements, like IDs, timestamps, or rankings.
- **Range Queries**: Efficiently perform range queries on a dataset, such as fetching elements within a specific range.

### Summary
- `SortedSet` is an interface that extends `Set` to maintain a sorted collection of unique elements.
- The `TreeSet` class is the primary implementation, leveraging a balanced tree structure to keep elements in order.
- `SortedSet` provides several methods for range operations, making it suitable for scenarios that require ordered, unique data access and manipulation.

Understanding `SortedSet` and its features can be beneficial for managing ordered, unique data in Java.
<br>
<br>
## **3. Map Interface in Java Collection Framework**
The **Map** interface in Java is a part of the **Java Collection Framework** and is used to store **key-value pairs**. Unlike collections such as `List` or `Set`, a `Map` does not allow duplicate keys; each key maps to a single value, but values can be duplicated.

### Key Characteristics of `Map`
1. **Key-Value Pairs**: Each entry in a `Map` consists of a unique key and a corresponding value.
2. **No Duplicate Keys**: Keys in a `Map` must be unique, but values may be duplicated.
3. **Null Keys and Values**: Some implementations, like `HashMap`, allow one `null` key and multiple `null` values, while others, like `Hashtable`, do not allow `null` keys or values.

### Common Implementations of `Map`
- **HashMap**: Uses a hash table, provides constant-time performance for most operations, allows `null` keys and values, and does not guarantee any order.
- **LinkedHashMap**: Maintains insertion order of keys.
- **TreeMap**: Stores keys in a sorted, ascending order (by natural ordering or custom comparator) and does not allow `null` keys.
- **Hashtable**: Synchronized, does not allow `null` keys or values, and is considered legacy (often replaced by `ConcurrentHashMap`).

### Key Methods in the `Map` Interface

| Method | Description |
|--------|-------------|
| `put(K key, V value)` | Associates the specified value with the specified key in the map. |
| `get(Object key)` | Returns the value associated with the specified key, or `null` if the map contains no mapping for the key. |
| `remove(Object key)` | Removes the mapping for a key if it is present. |
| `containsKey(Object key)` | Returns `true` if the map contains a mapping for the specified key. |
| `containsValue(Object value)` | Returns `true` if the map contains one or more keys mapped to the specified value. |
| `keySet()` | Returns a `Set` view of the keys contained in the map. |
| `values()` | Returns a `Collection` view of the values contained in the map. |
| `entrySet()` | Returns a `Set` view of the mappings (entries) contained in this map. |

### Example of Using `Map` with `HashMap`

Here’s an example that demonstrates basic operations on a `Map` using `HashMap`:

```java
import java.util.HashMap;
import java.util.Map;

public class MapExample {
    public static void main(String[] args) {
        // Creating a Map using HashMap
        Map<Integer, String> map = new HashMap<>();

        // Adding key-value pairs to the Map
        map.put(1, "Alice");
        map.put(2, "Bob");
        map.put(3, "Charlie");

        // Displaying the Map
        System.out.println("Map: " + map); // Output: Map: {1=Alice, 2=Bob, 3=Charlie}

        // Accessing values by key
        System.out.println("Key 2 maps to: " + map.get(2)); // Output: Key 2 maps to: Bob

        // Checking for a key or value
        System.out.println("Map contains key 1? " + map.containsKey(1)); // Output: true
        System.out.println("Map contains value 'Alice'? " + map.containsValue("Alice")); // Output: true

        // Iterating over entries
        for (Map.Entry<Integer, String> entry : map.entrySet()) {
            System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue());
        }

        // Removing a key-value pair
        map.remove(3);
        System.out.println("After removing key 3: " + map); // Output: {1=Alice, 2=Bob}
    }
}
```
**File 2**
<br>
<br>
```java
package CollectionFrameworkJava.Map;
import java.util.*;
public class MapDemp {
    public static void main(String[] args) {
        Employee emp1 = new Employee(101, "Ahamad");
        Employee emp2 = new Employee(102, "Aman");
        Employee emp3 = new Employee(103, "Usama");
        Employee emp4 = new Employee(104, "Hamza");
        Employee emp5 = new Employee(105, "Huzaifa");
        Employee emp6 = new Employee(106, "Salim");
        Employee emp7 = new Employee(107, "Siraj");
        Employee emp8 = new Employee(108, "Virat");
//        Map<Integer, String> company = new HashMap<>();
        HashMap<Integer, Employee> company = new HashMap<>();
        company.put(1, emp1);
        company.put(2, emp2);
        company.put(3, emp3);
        company.put(4, emp4);
        company.put(5, emp5);
        company.put(6, emp6);
        company.put(7, emp7);
        company.put(8, emp8);
        System.out.println(company);
        System.out.println("Get key value of " + company.get(5));

        System.out.println("To get keySet " + company.keySet());
        System.out.println("To get value "+ company.values() );

        for (int i = 0; i < company.size(); i++){
            System.out.println(company.get(i+1));
        }
        System.out.println("Is Map is Empty -- " + company.isEmpty()); // False

        // For Reaching Key value pair Method 1.
        Set<Map.Entry <Integer, Employee>> comp = company.entrySet();
        Iterator<Map.Entry<Integer, Employee>> com = comp.iterator();
        while (com.hasNext()){
            Map.Entry<Integer, Employee> kyvp = com.next();
            Integer iKey = kyvp.getKey();
            Employee skey = kyvp.getValue();
            System.out.println("Key" + iKey +", Value"+ skey);
        }
        // For Reaching Key value pair Method 2.
        for (Map.Entry<Integer, Employee> entry : company.entrySet()){
            System.out.println("Key " + entry.getKey() + ", Value " + entry.getValue());
        }
    }
}
class Employee {
    int id;
    String name;

    public Employee(){}
    public Employee(int id , String name){
        super();
        this.id = id;
        this.name = name;
    }

    @Override
    public String toString() {
        return "Employee{" +
                "id=" + id +
                ", name='" + name + '\'' +
                '}';
    }
}

```

### Example with `TreeMap` (Sorted by Keys)

If you need the keys to be sorted, use `TreeMap`:

```java
import java.util.Map;
import java.util.TreeMap;

public class TreeMapExample {
    public static void main(String[] args) {
        Map<String, Integer> treeMap = new TreeMap<>();

        // Adding key-value pairs
        treeMap.put("Apple", 5);
        treeMap.put("Banana", 2);
        treeMap.put("Cherry", 8);

        // TreeMap sorts keys in ascending order
        System.out.println("TreeMap: " + treeMap); // Output: {Apple=5, Banana=2, Cherry=8}

        // Accessing sorted keys
        for (Map.Entry<String, Integer> entry : treeMap.entrySet()) {
            System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue());
        }
    }
}
```

### Real-World Use Cases
- **Storing and Accessing Data by Key**: Useful for scenarios where you need fast lookups, such as caching data or storing user information.
- **Counting Occurrences**: Can be used to count occurrences of items, like counting word frequencies.
- **Maintaining Key-Value Relationships**: Useful for maintaining mappings between two related values, such as usernames and user IDs.

### Summary
- `Map` is a key-value collection that does not allow duplicate keys.
- Different implementations (`HashMap`, `TreeMap`, `LinkedHashMap`) serve different purposes, depending on whether order and performance are priorities.
- The `Map` interface provides efficient access to elements based on keys and offers methods for retrieving, updating, and removing entries.

## **4. SortedMap**
The `SortedMap` interface in Java extends the `Map` interface, providing a total ordering on its keys. This means that the keys are sorted either in their natural order or according to a specified comparator. The most commonly used implementation of `SortedMap` is `TreeMap`, which sorts keys in ascending order by default.

### Key Features of `SortedMap`

1. **Automatic Sorting**: Keys are automatically sorted.
2. **Range Views**: Provides methods to return subsets of the map (e.g., `headMap()`, `tailMap()`, and `subMap()`).
3. **First and Last Keys**: Allows retrieval of the smallest (`firstKey()`) and largest (`lastKey()`) keys.

### Basic Example of `SortedMap` in Java

Here’s a simple example that demonstrates the use of `SortedMap` with `TreeMap`:

```java
import java.util.SortedMap;
import java.util.TreeMap;

public class SortedMapExample {
    public static void main(String[] args) {
        // Creating a TreeMap that implements SortedMap
        SortedMap<Integer, String> sortedMap = new TreeMap<>();

        // Adding elements to the sorted map
        sortedMap.put(3, "Cherry");
        sortedMap.put(1, "Apple");
        sortedMap.put(4, "Date");
        sortedMap.put(2, "Banana");

        // Displaying the sorted map (keys are in ascending order)
        System.out.println("SortedMap: " + sortedMap);

        // Accessing the first and last keys
        System.out.println("First Key: " + sortedMap.firstKey());
        System.out.println("Last Key: " + sortedMap.lastKey());

        // Getting a view of the portion of the map whose keys are strictly less than a given key
        System.out.println("HeadMap (keys less than 3): " + sortedMap.headMap(3));

        // Getting a view of the portion of the map whose keys are greater than or equal to a given key
        System.out.println("TailMap (keys greater than or equal to 3): " + sortedMap.tailMap(3));

        // Getting a view of the portion of the map whose keys range from a starting key (inclusive) to an ending key (exclusive)
        System.out.println("SubMap (keys from 2 to 4): " + sortedMap.subMap(2, 4));
    }
}
```

### Explanation of Code

- **Creating a SortedMap**: A `TreeMap` is created, which implements `SortedMap`. The keys are sorted in ascending order by default.
- **Adding Elements**: `put()` is used to insert key-value pairs.
- **Sorted Order Display**: The `TreeMap` maintains the key order automatically.
- **Retrieving Boundaries**: `firstKey()` and `lastKey()` retrieve the smallest and largest keys.
- **Range Views**: 
  - `headMap(toKey)` returns keys strictly less than the specified key.
  - `tailMap(fromKey)` returns keys greater than or equal to the specified key.
  - `subMap(fromKey, toKey)` returns keys in a specified range, where `fromKey` is inclusive, and `toKey` is exclusive.

### Expected Output

```plaintext
SortedMap: {1=Apple, 2=Banana, 3=Cherry, 4=Date}
First Key: 1
Last Key: 4
HeadMap (keys less than 3): {1=Apple, 2=Banana}
TailMap (keys greater than or equal to 3): {3=Cherry, 4=Date}
SubMap (keys from 2 to 4): {2=Banana, 3=Cherry}
```

### Notes on `SortedMap` Implementations

- `TreeMap` is the only class that directly implements `SortedMap`.
- If you need a sorted map that requires custom ordering, you can pass a `Comparator` to the `TreeMap` constructor.

This example demonstrates the `SortedMap` interface with the `TreeMap` implementation and its ability to provide key ordering and range views.







