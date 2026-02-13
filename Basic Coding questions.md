# Basic Array Programs (Interview Ready)

## 1️⃣ Find Maximum Element

 Linear scan
 O(n)

```java
public static int findMax(int[] arr) {
    int max = arr[0];
    for (int num : arr) {
        if (num > max)
            max = num;
    }
    return max;
}
```

---

## 2️⃣ Find Minimum Element

 O(n)

```java
public static int findMin(int[] arr) {
    int min = arr[0];
    for (int num : arr) {
        if (num < min)
            min = num;
    }
    return min;
}
```

---

## 3️⃣ Find Second Largest Element

 Track two variables
 O(n)

```java
public static int secondLargest(int[] arr) {
    int first = Integer.MIN_VALUE;
    int second = Integer.MIN_VALUE;

    for (int num : arr) {
        if (num > first) {
            second = first;
            first = num;
        } else if (num > second && num != first) {
            second = num;
        }
    }
    return second;
}
```

---

## 4️⃣ Reverse an Array (In-place)

 O(n)

```java
public static void reverse(int[] arr) {
    int left = 0, right = arr.length - 1;
    while (left < right) {
        int temp = arr[left];
        arr[left] = arr[right];
        arr[right] = temp;
        left++;
        right--;
    }
}
```

---

## 5️⃣ Calculate Sum of Array

 O(n)

```java
public static int sum(int[] arr) {
    int sum = 0;
    for (int num : arr)
        sum += num;
    return sum;
}
```

---

## 6️⃣ Calculate Average

 O(n)

```java
public static double average(int[] arr) {
    int sum = 0;
    for (int num : arr)
        sum += num;
    return (double) sum / arr.length;
}
```

---

## 7️⃣ Count Even and Odd Numbers

 O(n)

```java
public static void countEvenOdd(int[] arr) {
    int even = 0, odd = 0;
    for (int num : arr) {
        if (num % 2 == 0)
            even++;
        else
            odd++;
    }
    System.out.println("Even: " + even + ", Odd: " + odd);
}
```

---

## 8️⃣ Search Element (Linear Search)

 O(n)

```java
public static int linearSearch(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target)
            return i;
    }
    return -1;
}
```

---

## 9️⃣ Binary Search (Sorted Array)

 O(log n)

```java
public static int binarySearch(int[] arr, int target) {
    int left = 0, right = arr.length - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == target)
            return mid;
        else if (arr[mid] < target)
            left = mid + 1;
        else
            right = mid - 1;
    }
    return -1;
}
```

---

## 🔟 Check if Array is Sorted

 O(n)

```java
public static boolean isSorted(int[] arr) {
    for (int i = 1; i < arr.length; i++) {
        if (arr[i] < arr[i - 1])
            return false;
    }
    return true;
}
```

---

## 1️⃣1️⃣ Count Occurrence of an Element

 O(n)

```java
public static int countOccurrences(int[] arr, int target) {
    int count = 0;
    for (int num : arr) {
        if (num == target)
            count++;
    }
    return count;
}
```

---

## 1️⃣2️⃣ Remove Duplicates (Using HashSet)

 O(n)

```java
public static int[] removeDuplicates(int[] arr) {
    Set<Integer> set = new HashSet<>();
    for (int num : arr)
        set.add(num);

    int[] result = new int[set.size()];
    int i = 0;
    for (int num : set)
        result[i++] = num;

    return result;
}
```

---

## 1️⃣3️⃣ Move Zeros to End

 O(n)

```java
public static void moveZeros(int[] arr) {
    int index = 0;
    for (int num : arr) {
        if (num != 0)
            arr[index++] = num;
    }
    while (index < arr.length)
        arr[index++] = 0;
}
```

---

## 1️⃣4️⃣ Rotate Array Right by 1

 O(n)

```java
public static void rotateRight(int[] arr) {
    int last = arr[arr.length - 1];
    for (int i = arr.length - 1; i > 0; i--)
        arr[i] = arr[i - 1];
    arr[0] = last;
}
```

---

## 1️⃣5️⃣ Rotate Array Left by 1

 O(n)

```java
public static void rotateLeft(int[] arr) {
    int first = arr[0];
    for (int i = 0; i < arr.length - 1; i++)
        arr[i] = arr[i + 1];
    arr[arr.length - 1] = first;
}
```

---

## 1️⃣6️⃣ Find Missing Number (1 to n)

 O(n)

```java
public static int findMissing(int[] arr, int n) {
    int total = n * (n + 1) / 2;
    int sum = 0;
    for (int num : arr)
        sum += num;
    return total - sum;
}
```

---

## 1️⃣7️⃣ Find Duplicate (Using Set)

 O(n)

```java
public static int findDuplicate(int[] arr) {
    Set<Integer> set = new HashSet<>();
    for (int num : arr) {
        if (!set.add(num))
            return num;
    }
    return -1;
}
```

---

## 1️⃣8️⃣ Find Intersection of Two Arrays

 O(n + m)

```java
public static Set<Integer> intersection(int[] a, int[] b) {
    Set<Integer> set1 = new HashSet<>();
    Set<Integer> result = new HashSet<>();

    for (int num : a)
        set1.add(num);

    for (int num : b) {
        if (set1.contains(num))
            result.add(num);
    }
    return result;
}
```

---

## 1️⃣9️⃣ Find Pair with Given Sum (Brute Force)

 O(n²)

```java
public static void pairSum(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        for (int j = i + 1; j < arr.length; j++) {
            if (arr[i] + arr[j] == target)
                System.out.println(arr[i] + ", " + arr[j]);
        }
    }
}
```

---

## 2️⃣0️⃣ Find Frequency of All Elements

 O(n)

```java
public static void frequency(int[] arr) {
    Map<Integer, Integer> map = new HashMap<>();
    for (int num : arr)
        map.put(num, map.getOrDefault(num, 0) + 1);

    for (Map.Entry<Integer, Integer> entry : map.entrySet())
        System.out.println(entry.getKey() + " -> " + entry.getValue());
}
```

---

## 1️⃣ Reverse a String

Two Pointer
O(n)

```java
public static String reverse(String str) {
    char[] arr = str.toCharArray();
    int left = 0, right = arr.length - 1;

    while (left < right) {
        char temp = arr[left];
        arr[left] = arr[right];
        arr[right] = temp;
        left++;
        right--;
    }
    return new String(arr);
}
```

---

## 2️⃣ Check Palindrome

 O(n)

```java
public static boolean isPalindrome(String str) {
    int left = 0, right = str.length() - 1;
    while (left < right) {
        if (str.charAt(left) != str.charAt(right))
            return false;
        left++;
        right--;
    }
    return true;
}
```

---

## 3️⃣ Count Vowels and Consonants

 O(n)

```java
public static void countVC(String str) {
    int vowels = 0, consonants = 0;
    str = str.toLowerCase();

    for (char ch : str.toCharArray()) {
        if (Character.isLetter(ch)) {
            if ("aeiou".indexOf(ch) != -1)
                vowels++;
            else
                consonants++;
        }
    }
    System.out.println("Vowels: " + vowels + ", Consonants: " + consonants);
}
```

---

## 4️⃣ Count Characters (Frequency)

 O(n)

```java
public static void frequency(String str) {
    Map<Character, Integer> map = new HashMap<>();
    for (char ch : str.toCharArray()) {
        map.put(ch, map.getOrDefault(ch, 0) + 1);
    }
    System.out.println(map);
}
```

---

## 5️⃣ Check Anagram

🧠 Sorting or Hashing
 O(n log n)

```java
public static boolean isAnagram(String s1, String s2) {
    char[] a = s1.toCharArray();
    char[] b = s2.toCharArray();
    Arrays.sort(a);
    Arrays.sort(b);
    return Arrays.equals(a, b);
}
```

---

## 6️⃣ Remove Duplicates

 O(n)

```java
public static String removeDuplicates(String str) {
    Set<Character> set = new LinkedHashSet<>();
    for (char ch : str.toCharArray())
        set.add(ch);

    StringBuilder sb = new StringBuilder();
    for (char ch : set)
        sb.append(ch);

    return sb.toString();
}
```

---

## 7️⃣ Find First Non-Repeating Character

 O(n)

```java
public static char firstNonRepeating(String str) {
    Map<Character, Integer> map = new LinkedHashMap<>();

    for (char ch : str.toCharArray())
        map.put(ch, map.getOrDefault(ch, 0) + 1);

    for (Map.Entry<Character, Integer> entry : map.entrySet()) {
        if (entry.getValue() == 1)
            return entry.getKey();
    }
    return '_';
}
```

---

## 8️⃣ Check if String Contains Only Digits

 O(n)

```java
public static boolean isNumeric(String str) {
    for (char ch : str.toCharArray()) {
        if (!Character.isDigit(ch))
            return false;
    }
    return true;
}
```

---

## 9️⃣ Convert String to Uppercase (Without Built-in)

 O(n)

```java
public static String toUpper(String str) {
    StringBuilder sb = new StringBuilder();
    for (char ch : str.toCharArray()) {
        if (ch >= 'a' && ch <= 'z')
            sb.append((char)(ch - 32));
        else
            sb.append(ch);
    }
    return sb.toString();
}
```

---

## 🔟 Count Words in a String

 O(n)

```java
public static int wordCount(String str) {
    str = str.trim();
    if (str.isEmpty()) return 0;
    return str.split("\\s+").length;
}
```

---

## 1️⃣1️⃣ Check Substring

 O(n)

```java
public static boolean contains(String str, String sub) {
    return str.indexOf(sub) != -1;
}
```

---

## 1️⃣2️⃣ Replace Spaces with %20

 O(n)

```java
public static String replaceSpaces(String str) {
    return str.replace(" ", "%20");
}
```

---

## 1️⃣3️⃣ Reverse Each Word

 O(n)

```java
public static String reverseWords(String str) {
    String[] words = str.split(" ");
    StringBuilder result = new StringBuilder();

    for (String word : words) {
        result.append(new StringBuilder(word).reverse()).append(" ");
    }
    return result.toString().trim();
}
```

---

## 1️⃣4️⃣ Remove Whitespaces

 O(n)

```java
public static String removeSpaces(String str) {
    return str.replaceAll("\\s", "");
}
```

---

## 1️⃣5️⃣ Find Duplicate Characters

 O(n)

```java
public static void findDuplicates(String str) {
    Map<Character, Integer> map = new HashMap<>();
    for (char ch : str.toCharArray())
        map.put(ch, map.getOrDefault(ch, 0) + 1);

    for (Map.Entry<Character, Integer> entry : map.entrySet()) {
        if (entry.getValue() > 1)
            System.out.println(entry.getKey());
    }
}
```

---

## 1️⃣6️⃣ Check Rotation of Another String

 O(n)

```java
public static boolean isRotation(String s1, String s2) {
    return s1.length() == s2.length() &&
           (s1 + s1).contains(s2);
}
```

---

## 1️⃣7️⃣ Toggle Case

 O(n)

```java
public static String toggleCase(String str) {
    StringBuilder sb = new StringBuilder();

    for (char ch : str.toCharArray()) {
        if (Character.isUpperCase(ch))
            sb.append(Character.toLowerCase(ch));
        else
            sb.append(Character.toUpperCase(ch));
    }
    return sb.toString();
}
```

---

## 1️⃣8️⃣ Find Longest Word

 O(n)

```java
public static String longestWord(String str) {
    String[] words = str.split(" ");
    String longest = "";

    for (String word : words) {
        if (word.length() > longest.length())
            longest = word;
    }
    return longest;
}
```

---

## 1️⃣9️⃣ Check If Two Strings Are Equal (Without equals())

 O(n)

```java
public static boolean isEqual(String s1, String s2) {
    if (s1.length() != s2.length()) return false;

    for (int i = 0; i < s1.length(); i++) {
        if (s1.charAt(i) != s2.charAt(i))
            return false;
    }
    return true;
}
```

---

## 2️⃣0️⃣ Remove Character from String

 O(n)

```java
public static String removeChar(String str, char ch) {
    StringBuilder sb = new StringBuilder();
    for (char c : str.toCharArray()) {
        if (c != ch)
            sb.append(c);
    }
    return sb.toString();
}
```

---

# ✅ Array Interview Questions – Techniques Summary Table

| #  | Problem                    | Technique Used        | Algorithm Strategy                | Time Complexity | Space Complexity |
| -- | -------------------------- | --------------------- | --------------------------------- | --------------- | ---------------- |
| 1  | Find Maximum               | Linear Traversal      | Track max while iterating         | O(n)            | O(1)             |
| 2  | Find Minimum               | Linear Traversal      | Track min while iterating         | O(n)            | O(1)             |
| 3  | Second Largest             | Two Variable Tracking | Maintain first & second max       | O(n)            | O(1)             |
| 4  | Reverse Array              | Two Pointer           | Swap from both ends               | O(n)            | O(1)             |
| 5  | Sum of Array               | Linear Traversal      | Accumulate sum                    | O(n)            | O(1)             |
| 6  | Average of Array           | Linear Traversal      | Sum ÷ length                      | O(n)            | O(1)             |
| 7  | Count Even/Odd             | Linear Traversal      | Check num % 2                     | O(n)            | O(1)             |
| 8  | Linear Search              | Linear Search         | Compare element by element        | O(n)            | O(1)             |
| 9  | Binary Search              | Binary Search         | Divide and conquer (sorted array) | O(log n)        | O(1)             |
| 10 | Check Sorted               | Linear Comparison     | Compare adjacent elements         | O(n)            | O(1)             |
| 11 | Count Occurrences          | Linear Traversal      | Increment counter                 | O(n)            | O(1)             |
| 12 | Remove Duplicates          | HashSet (Hashing)     | Store unique elements             | O(n)            | O(n)             |
| 13 | Move Zeros to End          | Two Pointer           | Shift non-zero forward            | O(n)            | O(1)             |
| 14 | Rotate Right by 1          | Shifting              | Move elements right               | O(n)            | O(1)             |
| 15 | Rotate Left by 1           | Shifting              | Move elements left                | O(n)            | O(1)             |
| 16 | Find Missing Number        | Mathematical Formula  | Sum formula n(n+1)/2              | O(n)            | O(1)             |
| 17 | Find Duplicate             | HashSet               | Detect duplicate via add()        | O(n)            | O(n)             |
| 18 | Intersection of Two Arrays | HashSet               | Store + lookup                    | O(n + m)        | O(n)             |
| 19 | Pair Sum (Brute)           | Nested Loop           | Check all pairs                   | O(n²)           | O(1)             |
| 20 | Frequency of Elements      | HashMap (Hashing)     | Count occurrences                 | O(n)            | O(n)             |

---

# Technique Distribution (Very Important for Interviews)

| Technique            | Used In Questions        |
| -------------------- | ------------------------ |
| Linear Traversal     | 1, 2, 5, 6, 7, 8, 10, 11 |
| Two Pointer          | 4, 13                    |
| Binary Search        | 9                        |
| Hashing (Set/Map)    | 12, 17, 18, 20           |
| Mathematical Formula | 16                       |
| Shifting Technique   | 14, 15                   |
| Nested Loop          | 19                       |

---


