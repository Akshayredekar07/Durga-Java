
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

