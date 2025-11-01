# Java String & StringBuilder Cheatsheet for LLD Rounds

## String Basics

### Creation
```java
String s1 = "hello";                    // String literal (from pool)
String s2 = new String("hello");        // New object on heap
String s3 = String.valueOf(123);        // From int/long/float/double/boolean
String s4 = String.valueOf(charArray);  // From char array
```

### Common String Operations

#### Length & Empty Check
```java
s.length()                  // Returns length
s.isEmpty()                 // true if length is 0
s.isBlank()                 // true if empty or only whitespace (Java 11+)
```

#### Character Access
```java
s.charAt(index)             // Get char at index
s.toCharArray()             // Convert to char[]
s.codePointAt(index)        // Get Unicode code point
```

#### Substring & Splitting
```java
s.substring(start)          // From start to end
s.substring(start, end)     // From start to end-1 (exclusive)
s.split(regex)              // Split by regex, returns String[]
s.split(regex, limit)       // Limit number of splits
```

#### Searching
```java
s.indexOf(ch)               // First occurrence of char
s.indexOf(str)              // First occurrence of substring
s.indexOf(str, fromIndex)   // Search from index
s.lastIndexOf(ch)           // Last occurrence
s.contains(str)             // true if contains substring
s.startsWith(prefix)        // Check prefix
s.endsWith(suffix)          // Check suffix
```

#### Comparison
```java
s1.equals(s2)               // Value equality
s1.equalsIgnoreCase(s2)     // Case-insensitive equality
s1.compareTo(s2)            // Lexicographic: negative/0/positive
s1.compareToIgnoreCase(s2)  // Case-insensitive compare
```

#### Case Conversion
```java
s.toLowerCase()             // Convert to lowercase
s.toUpperCase()             // Convert to uppercase
```

#### Trimming & Stripping
```java
s.trim()                    // Remove leading/trailing whitespace
s.strip()                   // Remove leading/trailing whitespace (Unicode-aware, Java 11+)
s.stripLeading()            // Remove leading whitespace (Java 11+)
s.stripTrailing()           // Remove trailing whitespace (Java 11+)
```

#### Replacing
```java
s.replace(oldChar, newChar)         // Replace all occurrences of char
s.replace(oldStr, newStr)           // Replace all occurrences of string
s.replaceAll(regex, replacement)    // Replace using regex
s.replaceFirst(regex, replacement)  // Replace first match
```

#### Matching
```java
s.matches(regex)            // true if entire string matches regex
```

#### Joining (Static Methods)
```java
String.join(delimiter, elements)           // Join with delimiter
String.join(", ", "a", "b", "c")          // "a, b, c"
String.join("-", list)                     // Join collection elements
```

#### Formatting (Static Methods)
```java
String.format("Hello %s", name)            // Format string
String.format("%d items", count)           // %d for int
String.format("%.2f", price)               // %.2f for 2 decimal places
```

#### Repetition
```java
s.repeat(count)             // Repeat string n times (Java 11+)
```

## StringBuilder Operations

### Creation
```java
StringBuilder sb = new StringBuilder();              // Empty, capacity 16
StringBuilder sb = new StringBuilder(capacity);      // With initial capacity
StringBuilder sb = new StringBuilder("initial");     // With initial string
```

### Append Operations
```java
sb.append(str)              // Append string
sb.append(ch)               // Append char
sb.append(num)              // Append int/long/float/double
sb.append(charArray)        // Append char array
sb.append(obj)              // Append object (calls toString())
```

### Insert Operations
```java
sb.insert(offset, str)      // Insert string at offset
sb.insert(offset, ch)       // Insert char at offset
sb.insert(offset, num)      // Insert number at offset
```

### Delete Operations
```java
sb.delete(start, end)       // Delete from start to end-1
sb.deleteCharAt(index)      // Delete char at index
```

### Replace
```java
sb.replace(start, end, str) // Replace range with string
sb.setCharAt(index, ch)     // Set char at index
```

### Reverse
```java
sb.reverse()                // Reverse the string
```

### Other Operations
```java
sb.length()                 // Current length
sb.capacity()               // Current capacity
sb.setLength(newLength)     // Set length (truncate or pad with null chars)
sb.charAt(index)            // Get char at index
sb.substring(start)         // Get substring (returns String)
sb.substring(start, end)    // Get substring from start to end-1
sb.toString()               // Convert to String
```

### Performance Tips
```java
// Pre-allocate capacity if you know approximate size
StringBuilder sb = new StringBuilder(expectedSize);

// Chaining methods
sb.append("Hello").append(" ").append("World");
```

## Common LLD Use Cases

### Building CSV/Delimited Strings
```java
StringBuilder sb = new StringBuilder();
for (int i = 0; i < items.size(); i++) {
    if (i > 0) sb.append(",");
    sb.append(items.get(i));
}
```

### Building JSON-like Strings
```java
StringBuilder json = new StringBuilder();
json.append("{")
    .append("\"name\":\"").append(name).append("\",")
    .append("\"age\":").append(age)
    .append("}");
```

### Reversing Words in a Sentence
```java
String[] words = s.split(" ");
StringBuilder sb = new StringBuilder();
for (int i = words.length - 1; i >= 0; i--) {
    sb.append(words[i]);
    if (i > 0) sb.append(" ");
}
```

### Removing Characters
```java
// Remove all spaces
String result = s.replace(" ", "");

// Remove specific characters
String result = s.replaceAll("[aeiou]", "");
```

### Checking Palindrome
```java
String cleaned = s.replaceAll("[^a-zA-Z0-9]", "").toLowerCase();
return cleaned.equals(new StringBuilder(cleaned).reverse().toString());
```

## Performance Notes

1. **String is immutable**: Every modification creates a new String object
2. **StringBuilder is mutable**: Modifies existing object, better for multiple operations
3. **StringBuffer**: Thread-safe version of StringBuilder (slower, use only if needed)
4. **When to use StringBuilder**:
    - Loops with string concatenation
    - Building complex strings with many operations
    - When performance matters
5. **String concatenation with +**: Compiler optimizes simple cases to StringBuilder

## Common Pitfalls

```java
// ❌ Bad: Creates many String objects in loop
String result = "";
for (String s : list) {
    result += s;  // Creates new String each iteration
}

// ✅ Good: Use StringBuilder
StringBuilder sb = new StringBuilder();
for (String s : list) {
    sb.append(s);
}
String result = sb.toString();

// ❌ Bad: Comparing with ==
if (s1 == s2)  // Compares references, not values

// ✅ Good: Use equals
if (s1.equals(s2))  // Compares actual content
```

## Regular Expression Quick Reference

```java
s.matches("\\d+")           // Only digits
s.matches("[a-zA-Z]+")      // Only letters
s.matches("\\w+")           // Word characters (letters, digits, _)
s.matches(".*@.*\\.com")    // Email-like pattern
s.replaceAll("\\s+", " ")   // Replace multiple spaces with single space
s.split("\\s+")             // Split by whitespace
```