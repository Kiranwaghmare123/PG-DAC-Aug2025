# Interview Questions
### 
    1.	What is Stream API in Java?
    2.	Difference between Collection and Stream?
    3.	What are intermediate and terminal operations?
    4.	What is lazy evaluation in streams?
    5.	How do you create a Stream?
    6.	What is the difference between map() and flatMap()?
    7.	What is filter() in streams?
    8.	What is the use of forEach()?
    9.	What is reduce()?
    10.	What is the difference between findFirst() and findAny()?
    11.	Difference between map() and peek()?
    12.	What is the difference between sorted() and distinct()?
    13.	How does collect() work?
    14.	What is Collectors.groupingBy()?
    15.	What is Collectors.partitioningBy()?
    16.	How to convert List to Map using streams?
    17.	How to handle duplicate keys while collecting to Map?
    18.	What is the difference between limit() and skip()?
    19.	What is Optional in Streams?
    20.	How do you handle NullPointerException in streams?
    21.	What is the difference between map() and flatMap() with real example?
    22.	What are parallel streams?
    23.	Difference between stream() and parallelStream()?
    24.	When should we NOT use parallel streams?
    25.	What is the ForkJoin framework in parallel streams?
    26.	Is Stream thread-safe?
    27.	What happens if you reuse a stream?
    28.	What is short-circuiting in streams?
    29.	Difference between reduce() and collect()?
    30.	How does internal iteration differ from external iteration?
 
 ### Coding-Based Interview Questions using streams
    1.	Find duplicate elements in a list
    2.	Find frequency of each character in a string
    3.	Find second highest number
    4.	Group employees by department
    5.	Find highest salary employee
    6.	Convert List<String> to comma-separated string
    7.	Merge two lists using streams
    8.	Flatten nested list
    9.	Count occurrences of words
    10.	Sort list by multiple fields

### Tricky Conceptual Questions
    •	Why are streams lazy?
    •	Can streams modify the source collection?
    •	What happens if an exception occurs in stream pipeline?
    •	Can we break from forEach()?
    •	What is stateful vs stateless intermediate operation?

---
# Notes:

Excellent choice! 🔥 Java Streams are a **must-master topic** for Java 8+ interviews — especially for backend developers working with Spring Boot like you.

Below are **well-structured technical interview notes** with properly listed methods and their usage.

---

#  Java Streams – Technical Interview Notes

---

# 1️⃣ What is Java Stream API?

The **Stream API** (introduced in Java 8) is used to process collections of objects in a **functional style**.

It supports:

* Declarative programming
* Internal iteration
* Parallel processing
* Functional operations (map, filter, reduce)

Streams do **not store data**. They operate on data from collections.

---

# 2️⃣ Stream vs Collection

| Collection          | Stream               |
| ------------------- | -------------------- |
| Stores data         | Does not store data  |
| External iteration  | Internal iteration   |
| Can modify elements | Cannot modify source |
| Eager execution     | Lazy execution       |

---

# 3️⃣ How to Create a Stream

```java
List<String> list = Arrays.asList("A", "B", "C");

// From Collection
Stream<String> stream = list.stream();

// Parallel stream
Stream<String> parallel = list.parallelStream();

// From Array
Stream<Integer> s = Arrays.stream(new Integer[]{1,2,3});

// Using Stream.of()
Stream<String> s2 = Stream.of("A","B","C");
```

---

# 4️ Stream Operations

There are **two types of operations**:

##  1. Intermediate Operations (Return Stream)

* Lazy
* Can be chained
* Executed only when terminal operation is called

##  2. Terminal Operations (Produce Result)

* End the pipeline
* Return value or side-effect

---

# 5️ Intermediate Methods (With Usage)

---

##  filter()

Filters elements based on condition.

```java
list.stream()
    .filter(x -> x.startsWith("A"))
    .collect(Collectors.toList());
```

---

##  map()

Transforms each element.

```java
list.stream()
    .map(String::toUpperCase)
    .collect(Collectors.toList());
```

Use when: 1 input → 1 output transformation

---

##  flatMap()

Flattens nested structure.

```java
List<List<String>> list = ...;

list.stream()
    .flatMap(Collection::stream)
    .collect(Collectors.toList());
```

Use when: 1 input → multiple outputs

---

##  distinct()

Removes duplicates.

```java
list.stream().distinct().collect(Collectors.toList());
```

---

##  sorted()

Sort elements.

```java
list.stream()
    .sorted()
    .collect(Collectors.toList());
```

Custom sorting:

```java
.sorted((a,b) -> a.compareTo(b))
```

---

##  peek()

Used for debugging.

```java
list.stream()
    .peek(System.out::println)
    .collect(Collectors.toList());
```

⚠ Not recommended for business logic.

---

##  limit()

Limit number of elements.

```java
stream.limit(5);
```

---

##  skip()

Skip first N elements.

```java
stream.skip(2);
```

---

# 6️ Terminal Methods (With Usage)

---

##  forEach()

Iterates elements.

```java
stream.forEach(System.out::println);
```

---

##  collect()

Most important method.

```java
stream.collect(Collectors.toList());
```

Common Collectors:

* toList()
* toSet()
* toMap()
* groupingBy()
* partitioningBy()
* joining()

---

##  reduce()

Performs aggregation.

```java
int sum = list.stream()
              .reduce(0, Integer::sum);
```

Use cases:

* Sum
* Multiplication
* Min/Max

---

##  count()

```java
long count = stream.count();
```

---

##  findFirst() / findAny()

```java
stream.findFirst();
stream.findAny();
```

Returns Optional.

---

##  anyMatch() / allMatch() / noneMatch()

```java
stream.anyMatch(x -> x > 10);
```

Short-circuiting operations.

---

##  min() / max()

```java
stream.max(Integer::compareTo);
```

---

# 7️ Collectors Important Methods

---

##  groupingBy()

```java
employees.stream()
         .collect(Collectors.groupingBy(Employee::getDepartment));
```

Returns Map<Department, List<Employee>>

---

##  partitioningBy()

Divides into two groups (true/false)

```java
stream.collect(Collectors.partitioningBy(x -> x > 10));
```

---

##  toMap()

```java
stream.collect(Collectors.toMap(
    Employee::getId,
    Employee::getName
));
```

Handle duplicates:

```java
Collectors.toMap(key, value, (oldVal, newVal) -> oldVal)
```

---

##  joining()

```java
stream.collect(Collectors.joining(","));
```

---

# 8️ Parallel Streams

```java
list.parallelStream()
```

Uses ForkJoinPool.

### When to use:

* Large dataset
* CPU-intensive operations
* No shared mutable state

### When NOT to use:

* Small dataset
* IO operations
* Stateful logic

---

# 9️ Important Interview Concepts

---

##  Lazy Evaluation

Intermediate operations execute only when terminal operation is called.

---

##  Short-Circuiting

Stops processing early.

Example:

* findFirst()
* anyMatch()
* limit()

---

##  Stateful vs Stateless

Stateless:

* map()
* filter()

Stateful:

* sorted()
* distinct()

---

##  Stream Reuse

Note: Stream cannot be reused.

```java
stream.forEach(...);
stream.forEach(...); // Exception
```

---

# Coding questions using streams


#  1️⃣ Find Duplicate Elements in a List

### Given a list of integers, find all duplicate elements.

###  Solution

```java
List<Integer> list = Arrays.asList(1,2,3,4,2,5,3,6);

Set<Integer> duplicates = list.stream()
        .collect(Collectors.groupingBy(
                Function.identity(),
                Collectors.counting()
        ))
        .entrySet()
        .stream()
        .filter(entry -> entry.getValue() > 1)
        .map(Map.Entry::getKey)
        .collect(Collectors.toSet());

System.out.println(duplicates);
```

###  Time Complexity

* Grouping: O(n)
* Filtering: O(n)
* Total: **O(n)**


---

#  2️⃣ Find Second Highest Number

### Find the second highest number in a list.

###  Solution

```java
List<Integer> list = Arrays.asList(10, 20, 30, 40, 50);

Optional<Integer> secondHighest = list.stream()
        .distinct()
        .sorted(Comparator.reverseOrder())
        .skip(1)
        .findFirst();

secondHighest.ifPresent(System.out::println);
```

###  Time Complexity

* distinct(): O(n)
* sorted(): O(n log n)
* Overall: **O(n log n)**


---

#  3️⃣ Group Employees by Department

### Group employees by department.

###  Solution

```java
Map<String, List<Employee>> grouped =
        employees.stream()
                .collect(Collectors.groupingBy(Employee::getDepartment));
```

###  Time Complexity

* Single pass grouping → **O(n)**


---

#  4️⃣ Find Highest Salary Employee

### Find employee with highest salary.

###  Solution

```java
Optional<Employee> highestSalary =
        employees.stream()
                .max(Comparator.comparing(Employee::getSalary));
```

###  Time Complexity

* Single traversal → **O(n)**


---

#  5️⃣ Count Frequency of Each Character in a String

### Count frequency of each character.

###  Solution

```java
String input = "java";

Map<Character, Long> frequency =
        input.chars()
                .mapToObj(c -> (char) c)
                .collect(Collectors.groupingBy(
                        Function.identity(),
                        Collectors.counting()
                ));
```

###  Time Complexity

* O(n)


---

#  6️⃣ Flatten a Nested List

### Convert List<List<Integer>> into single List<Integer>

### Solution

```java
List<List<Integer>> nested = Arrays.asList(
        Arrays.asList(1,2),
        Arrays.asList(3,4),
        Arrays.asList(5,6)
);

List<Integer> flat = nested.stream()
        .flatMap(List::stream)
        .collect(Collectors.toList());
```

###  Time Complexity

* Traverses all elements → **O(n)**


---

#  7️⃣ Partition Numbers into Even and Odd

### Separate even and odd numbers.

###  Solution

```java
Map<Boolean, List<Integer>> partition =
        list.stream()
                .collect(Collectors.partitioningBy(n -> n % 2 == 0));
```

###  Time Complexity

* Single pass → **O(n)**


---

#  8️⃣ Merge Two Lists Without Duplicates

### Merge two lists and remove duplicates.

###  Solution

```java
List<Integer> merged =
        Stream.concat(list1.stream(), list2.stream())
                .distinct()
                .collect(Collectors.toList());
```

###  Time Complexity

* Concat → O(n)
* distinct() → O(n)
* Total → **O(n)**

---

#  9️⃣ Find All Elements Starting with “A”

### Filter names starting with "A".

###  Solution

```java
List<String> result = names.stream()
        .filter(name -> name.startsWith("A"))
        .collect(Collectors.toList());
```

###  Time Complexity

* O(n)

---

#  🔟 Find Sum of All Numbers

### Find sum using reduce.

###  Solution

```java
int sum = list.stream()
        .reduce(0, Integer::sum);
```

OR

```java
int sum = list.stream()
        .mapToInt(Integer::intValue)
        .sum();
```

###  Time Complexity

* O(n)


---

#  Most Important Optimisation Insight

| Operation    | Complexity |
| ------------ | ---------- |
| filter()     | O(n)       |
| map()        | O(n)       |
| reduce()     | O(n)       |
| max()/min()  | O(n)       |
| groupingBy() | O(n)       |
| distinct()   | O(n)       |
| sorted()     | O(n log n) |

---



