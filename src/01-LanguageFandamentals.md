## **Language Fandamentals: Identifiers**

### **Question:** **How many Java identifiers are present in this code?**

```java
class Test {  
    public static void main(String args) {  
        int x = 10;  
        System.out.println(x);  
    }  
}
```

**Answer:** There are 6 identifiers. The list of identifiers is:

1. `Test`
2. `main`
3. `String`
4. `args`
5. `x`
6. `System`
7. `out`
8. `println`

---

## **Java Identifiers Rules**

### **1. Allowed Characters in Identifiers**  
In Java, an identifier can only contain the following characters:  
- `a-z` (lowercase letters)  
- `A-Z` (uppercase letters)  
- `0-9` (digits)  
- `_` (underscore)  
- `$` (dollar sign)  

**Examples:**  
```java
// Valid identifiers
int total_number = 100;
int total$amount = 200;
int TotalValue = 300;
int _count = 10;
int $price = 50;
```
**Note:** If we use any other character, we will get a compile-time error.  
```java
// Invalid identifiers (compile-time error)
int total#number = 100;
int @value = 200;
int 5count = 10;
```

---

### **2. Identifiers Cannot Start with Digits**  
In Java, an identifier cannot begin with a digit, though digits can be used after the first character.  

**Examples:**  
```java
// Valid identifier
int total123 = 500;
```
```java
// Invalid identifier (compile-time error)
int 123total = 600;
```

---

### **3. Case Sensitivity in Java Identifiers**  
Java is a **case-sensitive** programming language. Identifiers with different cases are treated as distinct.  

**Example:**  
```java
class Test {
    int number = 10;   // Lowercase
    int numer = 20;    // Different spelling
    int NUMBER30 = 30; // Uppercase variation
}
```
Here, `number`, `numer`, and `NUMBER30` are different variables due to case sensitivity.

---

### **4. No Length Limit for Java Identifiers**  
There is no specific length limit for Java identifiers. However, using excessively long identifiers is not recommended, as it makes the code harder to read and understand.  

**Examples:**  
```java
// Valid but not recommended due to length
int thisIsAVeryLongIdentifierThatIsHardToReadAndUnderstand = 100;
```
```java
// Recommended approach (short and meaningful)
int totalAmount = 100;
```

---

### **5. Reserved Words Cannot Be Used as Identifiers**  
Java does not allow the use of reserved keywords as identifiers.  

**Examples:**  
```java
// Valid identifier
int x = 10;
```
```java
// Invalid identifier (compile-time error)
int if = 20; // "if" is a reserved keyword
```

---

### **6. Predefined Java Class and Interface Names Can Be Used as Identifiers**  
In Java, predefined class names and interface names can be used as identifiers, but it is not recommended as it reduces code readability.  

**Examples:**  
```java
class Test {
    public static void main(String[] args) {
        int String = 888; // "String" is a predefined class but used as an identifier
        System.out.println(String); // Output: 888
    }
}
```
```java
class Test {
    public static void main(String[] args) {
        int Runnable = 999; // "Runnable" is an interface but used as an identifier
        System.out.println(Runnable); // Output: 999
    }
}
```
Even though it is valid, it is not good programming practice because it reduces readability and creates confusion.

---

### **Question: Valid Java Identifiers**  
Which of the following are valid Java identifiers?  

```java
- `total_number` // Valid  
- `total#` // Invalid  
- `123total` // Invalid  
- `ca$h` // Valid  
- `total123` // Valid  
- `_$_$_$_$total_number` // Valid  
- `all@hands` // Invalid  
- `java2share` // Valid  
- `Integer` // Valid  
- `IntegerInt` // Valid  
```
---

## **Java Reserved Words**  

In Java, some words are reserved to represent specific meanings or functionalities. These words are called **reserved words**.  

### **Total Reserved Words in Java: 53**  
- **Keywords: 50**  
  - **Used Keywords: 48**  
  - **Unused Keywords: 2 (`goto`, `const`)**  
- **Reserved Literals: 3 (`true`, `false`, `null`)**  

---

### **1. Keywords for Data Types (8)**  
`byte`, `short`, `int`, `long`, `boolean`, `char`, `float`, `double`  

### **2. Keywords for Flow Control (10)**  
`if`, `else`, `switch`, `case`, `default`, `while`, `do`, `for`, `break`, `continue`, `return`  

### **3. Keywords for Access Modifiers (11)**  
`public`, `private`, `protected`, `static`, `final`, `abstract`, `synchronized`, `native`, `volatile`, `transient`  

### **4. Keywords for Exception Handling (6)**  
`try`, `catch`, `finally`, `throw`, `throws`, `assert`  

### **5. Class-Related Keywords (6)**  
`class`, `interface`, `extends`, `implements`, `package`, `import`  

### **6. Object-Related Keywords (4)**  
`new`, `instanceof`, `super`, `this`  

### **7. Method-Related Keyword (1)**  
`void`  

- In Java, a return type is **mandatory**. If a method does not return anything, it must be declared as `void`.  
- In C, the return type is **optional**, and the default return type is `int`.  

---

### **8. Unused Keywords (2)**  
`goto`, `const`  

- **`goto`**: This keyword caused issues in older languages, so it was banned in Java.  
- **`const`**: Java uses `final` instead of `const`.  

Using `goto` or `const` in Java will result in a **compile-time error**.  

---

### **9. Reserved Literals (3)**  
`true`, `false`, `null`  

- `true`, `false` → Boolean values  
- `null` → Default value for object references  

---

### **10. Enum Keyword (Introduced in Java 1.5)**  
Used to define a group of named constants.  

**Example:**  
```java
enum Months {
    JAN, FEB, MAR, APR, MAY, JUN, JUL, AUG, SEP, OCT, NOV, DEC
}

enum Color {
    RED, GREEN, BLUE
}
```

---

### **11. Special Notes on Keywords**  
1. All **53 reserved words** contain only **lowercase** letters.  
2. Java has a `new` keyword but **no `delete` keyword**, as garbage collection automatically manages object destruction.  
3. Newly introduced keywords in Java:  
   - `strictfp` (Java 1.2)  
   - `assert` (Java 1.4)  
   - `enum` (Java 1.5)  

---

### **Question: Which of the following lists contain only Java reserved words?**  

```java
- `new, delete` // Invalid  
- `goto, constant` // Invalid  
- `break, continue, return, exit` // Invalid  
- `final, finally, finalize` // Invalid  
- `throw, throws, thrown` // Invalid  
- `notify, notifyAll` // Invalid  
- `implements, extends, imports` // Invalid  
- `sizeof, instanceof` // Invalid  
- `instanceOf, strictFp` // Invalid  
- `byte, short, Int` // Invalid  
- **None of the above** // Valid  
```

### **Question: Which of the following are Java reserved words?**  

- `public` // Valid (Reserved Word)  
- `static` // Valid (Reserved Word)  
- `void` // Valid (Reserved Word)  
- `main` // Invalid (Not a Reserved Word)  
- `String` // Invalid (Not a Reserved Word, it is a predefined class)  
- `args` // Invalid (Not a Reserved Word, it is just a variable name)  
