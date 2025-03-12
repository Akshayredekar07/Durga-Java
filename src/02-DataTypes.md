
## **Data Types in Java**  

In Java, every variable and expression must have a specific type. Without a type, a variable or expression cannot exist.

For example, the `byte` data type is **8 bits** in size and has a range from **-128 to 127**. 
In Java, you must assign values to variables that match their data type.

#### **Examples of Invalid Assignments in Java**  
- `int x = 10.5;` // **Invalid** because `10.5` is a floating-point value, but `int` only accepts whole numbers.  
- `boolean b = 0;` // **Invalid** because Java does not allow numeric values for Boolean types. A Boolean variable can only be `true` or `false`.  

In **C programming**, both of these cases would be valid, but Java enforces strict type checking at compile time. Every assignment is checked to ensure it follows type compatibility rules.  

Due to these strict type enforcement rules, Java is classified as a **strongly typed programming language**.  

---

### **Is Java a Pure Object-Oriented Programming Language?**  

No, Java is **not** considered a pure object-oriented programming language. While Java follows object-oriented principles, it does not enforce **everything as an object**, which is a key requirement for a pure object-oriented language.  

#### **Reasons Why Java is Not Purely Object-Oriented**  

1. **Primitive Data Types**  
   - Java supports **primitive types** like `int`, `char`, `boolean`, and `double`, which are **not objects**.  
   - A pure object-oriented language treats everything as an object.  

2. **Lack of Operator Overloading**  
   - Java does **not** allow operator overloading, unlike languages such as C++.  
   - In a purely object-oriented language, operators can be customized to work with objects.  

3. **No Multiple Inheritance with Classes**  
   - Java does **not** support multiple inheritance using classes due to ambiguity issues.  
   - It provides **interfaces** as an alternative, but a pure object-oriented language should support multiple inheritance directly.  

4. **Static Methods**  
   - Java allows **static methods**, which belong to a class rather than an instance.  
   - A pure object-oriented language ensures that every method operates on an object.  

#### **Conclusion**  
Java is **object-oriented**, but it is **not purely object-oriented** because it allows primitives, lacks certain OOP features, and permits static methods.  

---

## **Primitive Data Types in Java**  

In Java, **primitive data types** are the basic building blocks that store simple values directly in memory.  

#### **1. Numeric Data Types**  
- **Integral Data Types**: `byte`, `short`, `int`, `long`  
- **Floating-Point Data Types**: `float`, `double`  

#### **2. Non-Numeric Data Types**  
- **Character Data Type**: `char`  
- **Boolean Data Type**: `boolean`  

#### **Examples**  
```java
int x = 10;    // Valid  
int x = -10;   // Valid  
double d = 10.4;  // Invalid (misspelled as "dubble", should be "double")  

char ch = 'a';   // Valid  
boolean b = false;   // Valid  
```  

#### **Signed vs. Unsigned Data Types**  
- All numeric data types in Java **except `boolean` and `char`** are **signed**, meaning they can store both **positive and negative values**.  

---

## **Byte Data Type**  

The `byte` data type in Java is an **8-bit signed integer**. 
It is mainly used to save memory in large arrays where memory savings are crucial.  

- **Size**: The `byte` type occupies 1 byte (8 bits) of memory. This compact size makes it useful for saving memory in large arrays.

- **Sign Bit (MSB - Most Significant Bit)**: The first bit in the `byte` type is considered the sign bit. If the sign bit is `0`, the number is positive. If the sign bit is `1`, the number is negative.

- **Storage Mechanism**: Positive numbers are stored directly in memory, while negative numbers are stored in 2’s complement form. This allows for efficient arithmetic operations and representation of negative values.
- **Minimum Value**: `-128` (most significant bit `1` indicates negative).
- **Maximum Value**: `127` (most significant bit `0` indicates positive).
- **Range**: `-128` to `127`, useful for memory-efficient applications.

---

### **Binary Representation of `byte` Type**
```
| Sign Bit | 2^6 | 2^5 | 2^4 | 2^3 | 2^2 | 2^1 | 2^0 |
|----------|-----|-----|-----|-----|-----|-----|-----|
|    X     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |
```
- **If MSB (sign bit) = 0**, the number is **positive**.  
- **If MSB (sign bit) = 1**, the number is **negative** (stored as 2's complement).  

---

### **Example Calculation (Binary to Decimal)**  
For `01111111` (where sign bit is `0`):  
$$
64 + 32 + 16 + 8 + 4 + 2 + 1 = 127
$$
Thus, the maximum value is **127**.  

For `10000000` (where sign bit is `1`):  
This is stored in **2’s complement**, representing **-128**.  

Thus, **byte values range from -128 to 127** in Java.  

---

### **Valid and Invalid Declarations**  

#### **Valid Declarations**  
```java
byte b = 10;   // Valid
byte b = 127;  // Valid
```

#### **Invalid Declarations and Errors**  
```java
byte b = 128;   // Invalid (possible loss of precision)
                // Error: found int, required: byte

byte c = 10.5;  // Invalid (possible loss of precision)
                // Error: found double, required: byte

byte b = true;  // Invalid (incompatible types)
                // Error: found boolean, required: byte

byte b = "durga";  // Invalid (incompatible types)
                   // Error: found java.lang.String, required: byte
```
Java enforces **strict type checking**, and all assignments must match the declared data type without implicit conversions.  


### **Where to Use the `byte` Data Type?**

The `byte` data type is primarily used when handling **streams of data** from a **network** or **file system**.  

---

### **Types of Streams in Java**
1. **Character Stream** (Handles text data)  
2. **Byte Stream** (Handles raw binary data)  

---

### **Use Case: File and Network Operations**
- The **byte stream** is used when working with **files** and **network communication**.  
- It is efficient when handling **raw data**, such as **image files, audio files, or binary data**.

Example:  
```java
FileOutputStream fos = new FileOutputStream("output.txt");
byte[] data = {65, 66, 67}; // Corresponds to 'A', 'B', 'C'
fos.write(data);
fos.close();
```
---

##**`short` Data Type in Java**

The `short` data type is **rarely used** in Java because modern processors have outgrown its usefulness.

---

### **Size and Range**
- **Size**: 2 bytes (16 bits)  
- **Range**: -32,768 to 32,767 (`-2^15` to `2^15 - 1`)  
- **Max Value**: 32,767  
- **Min Value**: -32,768  

---

### **Examples**
```java
short s1 = 10;      // Valid
short s2 = 32767;   // Valid
short s3 = 32768;   // Invalid (Possible loss of precision: int required, found short)
short s4 = 10.5;    // Invalid (Possible loss of precision: double required, found short)
short s5 = "durga";  // Invalid (incompatible types found java.lang.String, required: short)
```

---

### **When is `short` Best Suitable?**
- Java was developed in **1995**, when **16-bit microprocessors** (e.g., **8085, 8086**) were widely used.  
- At that time, `short` was useful because **16-bit processors** could efficiently handle 2-byte data.  
- **However, modern processors are mostly 32-bit or 64-bit**, making `short` largely **obsolete**.  

Thus, `short` is rarely used in real-world Java applications.

---
## **`int` Data Type**

The `int` data type is the **most commonly used** data type in Java. It is used to store integer values.


### **Size and Range**
- **Size**: 4 bytes (32 bits)  
- **Range**: -2,147,483,648 to 2,147,483,647 (`-2^31` to `2^31 - 1`)  


### **Examples**
```java
int x = 2147483647;   // Valid
int y = 2147483648;   // Invalid (Compiler error: integer number too large)
int z = 2147483648l;  // Invalid (Compiler error: possible loss of precision, found: long required: int)
int a = 2147483648L;  // Valid

int x = true;         // Invalid (Compiler error: incompatible types: boolean cannot be converted to int)
int y = 1.0;         // Invalid (Compiler error: possible lossy conversion from double to int)
int z = 'a';         // Valid (ASCII value of 'a' is 97)
int a = 1.0f;        // Invalid (Compiler error: possible lossy conversion from float to int)
```

### **Why is `'a'` a valid integer?**
- In Java, characters are stored as **Unicode values**.
- `'a'` has an **ASCII value of 97**, which can be stored in an `int`.

Thus, `int z = 'a';` is **valid**, and `z` will store **97**.

---

## **`long` Data Type**

Sometimes, an `int` may not be sufficient to store a large numerical value. In such cases, we should use the `long` data type.

### **Size and Range**
- **Size**: 8 bytes (64 bits)  
- **Range**: `-2^63` to `2^63 - 1`

---

### **Use Cases**
1. **Storing large numerical values**  
   Example: The **distance traveled by light in a thousand days** may exceed the `int` range.
   ```java
   long l = 126_000 * 60 * 60 * 24;  // Valid
   ```
   
2. **Handling large file sizes**  
   Example: The number of characters in a large file may exceed the `int` range.
   ```java
   long l = f.length();  // Returns file length as long
   ```


- If an integer literal exceeds the `int` range, it **must** be suffixed with `L` or `l`.
  ```java
  long x = 2147483648;   // Invalid (Compiler error: integer number too large)
  long y = 2147483648L;  // Valid
  ```

- All **integral data types** (`byte`, `short`, `int`, `long`) are meant for representing **whole numbers**.
- If we need to store **floating-point numbers**, we must use `float` or `double`.

---

## **Floating-Point Data Types**

Floating-point data types are used to represent **decimal numbers** in Java. Java provides two floating-point types: **`float`** and **`double`**, which differ in size, precision, and accuracy.


### **1. `float` (Single Precision)**
- **Use Case**: When we need **5 to 6 decimal places** of accuracy.
- **Precision**: **Single Precision (32-bit)**
- **Size**: 4 bytes (32 bits)
- **Range**: `±3.4 × 10³⁸` to `±1.4 × 10⁻⁴⁵`
- **Performance**: Faster computation, less precise.
- **Example Usage**:
  ```java
  float f1 = 10.5f;   // Valid (must use 'f' or 'F' suffix)
  float f2 = 10.5;    // Invalid (possible lossy conversion from double to float)
  float f3 = 3.1415926535f;  // Valid but loses precision
  ```
- **Example Output**:
  ```java
  public class FloatExample {
      public static void main(String[] args) {
          float num = 3.1415926535f;
          System.out.println(num);  // Output: 3.1415927 (Precision loss)
      }
  }
  ```

---

### **2. `double` (Double Precision)**
- **Use Case**: When we need **14 to 15 decimal places** of accuracy.
- **Precision**: **Double Precision (64-bit)**
- **Size**: 8 bytes (64 bits)
- **Range**: `±1.7 × 10³⁰⁸` to `±4.9 × 10⁻³²⁴`
- **Performance**: Slower than `float`, but more precise.
- **Example Usage**:
  ```java
  double d1 = 10.5;   // Valid (default type for decimal numbers)
  double d2 = 3.141592653589793;  // More accurate than float
  ```
- **Example Output**:
  ```java
  public class DoubleExample {
      public static void main(String[] args) {
          double num = 3.141592653589793;
          System.out.println(num);  // Output: 3.141592653589793 (More precise)
      }
  }
  ```

---

### **3. Key Differences Between `float` and `double`**
| Feature  | `float` | `double` |
|----------|--------|----------|
| Precision | Single (32-bit) | Double (64-bit) |
| Accuracy  | 5-6 decimal places | 14-15 decimal places |
| Default Type | No (requires `f` suffix) | Yes |
| Suitable for | Less precision, memory-efficient | High precision calculations |
| Speed | Faster computation | Slower but more accurate |



### **4. Important Notes**
#### **By Default, Java Treats Decimal Numbers as `double`**
```java
float f = 10.5;   // Invalid (possible lossy conversion from double to float)
float f = 10.5f;  // Valid
```

#### **Floating-Point Division Behavior**
```java
double d = 10.0 / 3;  // Output: 3.3333333333333335 (high precision)
float f = 10.0f / 3;  // Output: 3.3333333 (lower precision)
```

#### **Scientific Notation Representation**
Both `float` and `double` can store values in **scientific notation**:
```java
float f = 3.4e10f;   // 3.4 × 10¹⁰
double d = 1.7e308;  // 1.7 × 10³⁰⁸
```

#### **Precision Loss Example**
```java
public class PrecisionLoss {
    public static void main(String[] args) {
        float f = 123456789.123456789f;
        double d = 123456789.123456789;

        System.out.println("Float: " + f);   // Output: 1.23456792E8
        System.out.println("Double: " + d);  // Output: 1.2345678912345679E8
    }
}
```
**Observation**: `float` loses precision after the 7th digit, while `double` retains more precision.

### **5. When to Use `float` vs. `double`?**
- **Use `float`** when:
  - Memory is limited.
  - You don't need extreme precision (e.g., graphics, game physics).
- **Use `double`** when:
  - High precision is required (e.g., scientific calculations, financial apps).
  - Computational accuracy is more important than speed.

---

## **Boolean Data Type**

The `boolean` data type in Java represents **true** or **false** values. Unlike numeric data types, `boolean` does not have a fixed size in memory—it is **JVM-dependent**.


### **1. Characteristics of `boolean`**
- **Size**: Not applicable (JVM-dependent)
- **Range**: Not applicable (only `true` and `false` are allowed)
- **Allowed Values**: `true` or `false` (case-sensitive)


### **2. Valid and Invalid `boolean` Assignments**
| Statement | Valid/Invalid | Reason |
|-----------|--------------|--------|
| `boolean b = true;`  | Valid  | `true` is a valid boolean value |
| `boolean b = false;` | Valid  | `false` is a valid boolean value |
| `boolean b = 0;` | Invalid | `int` cannot be converted to `boolean` |
| `boolean b = 1;` | Invalid | `int` cannot be converted to `boolean` |
| `boolean b = True;` | Invalid | `True` is not a valid keyword (`true` is lowercase) |
| `boolean b = "True";` | Invalid | String `"True"` cannot be converted to `boolean` |
| `boolean b = 'true';` | Invalid | Char `'true'` is not a valid boolean value |

---

### **3. Example Code: Valid and Invalid Boolean Declarations**
```java
public class BooleanExamples {
    public static void main(String[] args) {
        // Correct way to declare and initialize a boolean variable
        boolean b1 = true;  
        boolean b2 = false;

        // System.out.println(b1);  // Output: true
        // System.out.println(b2);  // Output: false

        // Invalid examples (Uncomment to see compilation errors)
        // boolean b3 = 1;   // Error: incompatible types: int cannot be converted to boolean
        // boolean b4 = "True"; // Error: incompatible types: String cannot be converted to boolean
        // boolean b5 = 'true'; // Error: incompatible types: char cannot be converted to boolean
    }
}
```

---

### **4. Boolean in Conditional Statements**
Unlike C, Java does **not** allow non-boolean values in conditions.

#### **Invalid Example: Assigning `int` to `boolean` in an `if` Condition**
```java
public class Test {
    public static void main(String[] args) {
        int x = 0;

        if (x) {  // Compilation Error: incompatible types: int cannot be converted to boolean
            System.out.println("Hello");
        } else {
            System.out.println("Hi");
        }
    }
}
```

#### **Invalid Example: Using `int` in a `while` Loop**
```java
public class LoopTest {
    public static void main(String[] args) {
        while (1) {  // Compilation Error: incompatible types: int cannot be converted to boolean
            System.out.println("Hello");
        }
    }
}
```
In **C language**, both cases are valid because C allows integers (`0` as false, non-zero as true) in conditions.  
In **Java**, these cases are **invalid** because Java is a **strongly-typed language**, requiring explicit `boolean` values.

---

### **5. Correct Boolean Usage in Java**
```java
public class BooleanCondition {
    public static void main(String[] args) {
        boolean isJavaFun = true;
        
        if (isJavaFun) {
            System.out.println("Yes, Java is fun!");  // Output: Yes, Java is fun!
        } else {
            System.out.println("No, Java is not fun.");
        }
    }
}
```

---

## **Character (`char`) Data Type**

The `char` data type in Java is used to store a **single character**. Unlike C or C++, where `char` is **1 byte**, Java's `char` is **2 bytes** because Java follows the **Unicode character set**.


### **1. Why is `char` 2 Bytes in Java?**  
Java follows the **Unicode** character set, which is a **16-bit encoding system**. This allows Java to represent **worldwide characters**, including languages such as Hindi, Marathi, Telugu, Gujarati, and many more. In contrast, **C and C++ use the ASCII character set**, which is **8-bit** and requires only **1 byte** to store characters. Since Java supports a much larger set of characters, it requires **2 bytes** to store a `char`.  


### **2. ASCII vs Unicode**  
In **C and C++**, the `char` data type follows the **ASCII** character set, which supports only **256 characters**, including English letters (`A-Z`, `a-z`), digits (`0-9`), and special symbols (`@`, `#`, `$`, etc.). Since 256 characters require only **8 bits (1 byte)**, the size of `char` in **C/C++ is 1 byte**.  

However, **Java uses Unicode**, which includes **all ASCII characters** along with additional characters from multiple languages. For example, Java supports:  
- **Hindi characters**: अ, ब, क, म, र  
- **Gujarati characters**: અ, બ, ક, મ, ર  
- **Punjabi characters**: ਅ, ਬ, ਕ, ਮ, ਰ  
- **Telugu characters**: అ, బ, క, మ, ర  

Since the number of **unique Unicode characters exceeds 256 and is less than 65536**, Java requires **16 bits (2 bytes)** to represent a `char`.  


### **3. Size and Range of `char` in Java**  
In Java, the **size of `char` is 2 bytes (16 bits)**. The **range of `char` is from `0` to `65535` (`0x0000` to `0xFFFF`)**, allowing representation of a vast set of characters from different languages.  

---

### **4. Valid and Invalid `char` Declarations**
| Statement | Valid/Invalid | Reason |
|-----------|--------------|--------|
| `char ch = 'a';` | Valid | A single character is allowed |
| `char ch = 'A';` | Valid | Uppercase character is allowed |
| `char ch = '0';` | Valid | A digit is a valid character |
| `char ch = 'abc';` | Invalid | More than one character (`unclosed character literal` error) |
| `char ch = 65;` | Valid | ASCII value `65` represents `'A'` |
| `char ch = 999;` | Valid | Unicode character at `999` is allowed |
| `char ch = -5;` | Invalid | Negative values are not allowed |
| `char ch = 45.6;` | Invalid | `double` cannot be assigned to `char` |

---

### **5. Example Code: Valid and Invalid `char` Declarations**
```java
public class CharExample {
    public static void main(String[] args) {
        // Valid char declarations
        char ch1 = 'a';  // Single character
        char ch2 = 'Z';  // Uppercase character
        char ch3 = '9';  // Digit
        char ch4 = 65;   // ASCII value (65 = 'A')
        char ch5 = 999;  // Unicode character at 999

        System.out.println("ch1: " + ch1);  // Output: a
        System.out.println("ch2: " + ch2);  // Output: Z
        System.out.println("ch3: " + ch3);  // Output: 9
        System.out.println("ch4: " + ch4);  // Output: A
        System.out.println("ch5: " + ch5);  // Output: corresponding Unicode character

        // Invalid declarations (Uncomment to see errors)
        // char ch6 = 'abc';  // Error: unclosed character literal
        // char ch7 = -5;    // Error: incompatible types: possible lossy conversion from int to char
        // char ch8 = 45.6;  // Error: incompatible types: possible lossy conversion from double to char
    }
}
```
---

### _**Java Primitive Data Types**_

### **Primitive Data Types in Java**
- **Size:** Memory allocated for each data type.
- **Range:** The minimum and maximum values that can be stored.
- **Wrapper Class:** The corresponding class in Java's `java.lang` package.
- **Default Value:** The default value when a variable is not explicitly initialized.

---

### **Table: Java Primitive Data Types**
#### **Integral Data Types**
- Used to store whole numbers.

#### **Floating-Point Data Types**
- Used to store decimal values.

#### **Character and Boolean Data Types**
- `char` stores single characters using Unicode.
- `boolean` stores logical values (`true` or `false`).

---
| **Data Type** | **Size**  | **Range / Allowed Values**                         | **Wrapper Class** | **Default Value** |
|--------------|----------|------------------------------------------------|-----------------|----------------|
| `byte`      | 1 byte   | -2⁷ to 2⁷-1 (-128 to 127)                      | `Byte`          | 0              |
| `short`     | 2 bytes  | -2¹⁵ to 2¹⁵-1 (-32,768 to 32,767)              | `Short`         | 0              |
| `int`       | 4 bytes  | -2³¹ to 2³¹-1 (-2,147,483,648 to 2,147,483,647) | `Integer`       | 0              |
| `long`      | 8 bytes  | -2⁶³ to 2⁶³-1                                  | `Long`          | 0              |
| `float`     | 4 bytes  | ±3.4028 × 10³⁸ to ±1.4 × 10⁻⁴⁵                 | `Float`         | 0.0            |
| `double`    | 8 bytes  | ±1.79 × 10³⁰⁸ to ±4.9 × 10⁻³²⁴                 | `Double`        | 0.0            |
| `char`      | 2 bytes  | 0 to 65535 (Unicode characters)                 | `Character`     | `\u0000` (null character) |
| `boolean`   | N/A      | `true` or `false`                               | `Boolean`       | `false`        |
---

### **Example Usage**
```java
public class DataTypeExample {
    public static void main(String[] args) {
        byte b = 127;          // Valid, within range
        short s = 32000;       // Valid
        int i = 2147483647;    // Valid
        long l = 9223372036854775807L; // Valid, 'L' suffix required for long

        float f = 3.14f;       // Valid, 'f' suffix required for float
        double d = 3.14159265358979; // Valid

        char c = 'A';          // Valid
        boolean bool = true;   // Valid

        System.out.println("Byte: " + b);
        System.out.println("Short: " + s);
        System.out.println("Int: " + i);
        System.out.println("Long: " + l);
        System.out.println("Float: " + f);
        System.out.println("Double: " + d);
        System.out.println("Char: " + c);
        System.out.println("Boolean: " + bool);
    }
}
```
---

### **`null` as the Default Value for Objects in Java**
- In Java, `null` is the **default value for reference types (objects)**.
- Primitive data types (`int`, `double`, `boolean`, etc.) **cannot be assigned `null`**.
- If we attempt to assign `null` to a primitive, **we get a compile-time error**.


### **Example: Assigning `null` to Primitives (Invalid)**
```java
public class NullExample {
    public static void main(String[] args) {
        int num = null;   // Compilation Error: incompatible types: <null> cannot be converted to int
        double d = null;  // Compilation Error
        boolean b = null; // Compilation Error
    }
}
```


### **Example: Assigning `null` to Objects (Valid)**
```java
public class NullObjectExample {
    public static void main(String[] args) {
        String str = null;  // Valid, String is an object
        Integer number = null; // Valid, Integer is a wrapper class

        System.out.println("String: " + str);
        System.out.println("Integer: " + number);
    }
}
```

### **Why Can't Primitives Hold `null`?**
- Primitive data types store **actual values** directly in memory.
- Objects store **references to memory locations**.
- `null` represents the **absence of an object reference**, so it **cannot be assigned to primitive types**.

---