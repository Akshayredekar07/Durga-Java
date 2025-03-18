
## **Command Line Arguments in Java**

The arguments passed from the command prompt while executing a Java program are called **command-line arguments**.

- When a Java program runs with command-line arguments, the **Java Virtual Machine (JVM)** creates an array (`args[]`) and passes it to the `main` method.
- The primary purpose of command-line arguments is to customize the program's behavior by providing different values during execution.

---

### **Example 1: Basic Command-Line Argument Usage**

This example demonstrates accessing a single command-line argument and performing a simple calculation.

#### **Code:**
```java
public class Test {
    public static void main(String[] args) {
        int n = Integer.parseInt(args[0]);
        System.out.println("The square of " + n + " is " + (n * n));
    }
}
```

#### **Execution Command:**
```sh
javac Test.java
java Test 5
```

#### **Output:**
```
The square of 5 is 25
```

#### **Note:**
- If no arguments are provided (e.g., `java Test`), the program will throw an **`ArrayIndexOutOfBoundsException`** because it attempts to access `args[0]` without verifying its existence.

---

### **Example 2: Iterating Over Command-Line Arguments**

This example shows how to iterate over all provided command-line arguments using a loop.

#### **Code:**
```java
public class Test {
    public static void main(String[] args) {
        for (int i = 0; i < args.length; i++) {
            System.out.println(args[i]);
        }
    }
}
```

#### **Execution Commands and Outputs:**

1. **Command:**
   ```sh
   javac Test.java
   java Test A B C
   ```
   **Output:**
   ```
   A
   B
   C
   ```

2. **Command:**
   ```sh
   java Test "RE: AJOOBE" A B
   ```
   **Output:**
   ```
   RE: AJOOBE
   A
   B
   ```

3. **Command:**
   ```sh
   java Test "RE: AJOOBE"
   ```
   **Output:**
   ```
   RE: AJOOBE
   ```

4. **Command:**
   ```sh
   java Test
   ```
   **Output:**
   *(No output, as the loop does not execute when `args.length` is 0)*

#### **Correction and Note:**
- The original text incorrectly states that `java Test` results in an **`ArrayIndexOutOfBoundsException`**. With the given loop condition (`i < args.length`), the program safely handles zero arguments because the loop does not execute.
- The note about replacing `<=` with `<` seems misplaced here, as the code already uses `<` and avoids accessing invalid indices.

---

### **Example 3: Assigning a New Array to `args`**

This example illustrates how reassigning the `args` array inside the program affects its behavior.

#### **Code:**
```java
public class Test {
    public static void main(String[] args) {
        String[] argh = {"x", "y", "z"};
        args = argh;
        for (String s : args) {
            System.out.println(s);
        }
    }
}
```

#### **Execution Commands and Outputs:**

1. **Command:**
   ```sh
   javac Test.java
   java Test A B C
   ```
   **Output:**
   ```
   x
   y
   z
   ```

2. **Command:**
   ```sh
   java Test A B
   ```
   **Output:**
   ```
   x
   y
   z
   ```

3. **Command:**
   ```sh
   java Test
   ```
   **Output:**
   ```
   x
   y
   z
   ```

#### **Explanation:**
- Regardless of the command-line arguments, the output remains `x y z` because the program overwrites `args` with a new array (`{"x", "y", "z"}`) before printing.

---

### **Example 4: Concatenation of Command-Line Arguments**

This example demonstrates how command-line arguments are treated as strings by default.

#### **Code:**
```java
public class Test {
    public static void main(String[] args) {
        System.out.println(args[0] + args[1]);
    }
}
```

#### **Execution Command:**
```sh
javac Test.java
java Test 10 20
```

#### **Output:**
```
1020
```

#### **Explanation:**
- Since `args[0]` and `args[1]` are strings (`"10"` and `"20"`), the `+` operator performs **string concatenation**, resulting in `"1020"`, not arithmetic addition.

---

### **Example 5: Handling Spaces in Command-Line Arguments**

This example highlights how spaces are interpreted in command-line arguments and the role of quotation marks.

#### **Key Points:**
- By default, **spaces** separate command-line arguments.
- To include spaces within a single argument, enclose it in **double quotes** (`""`).

#### **Code:**
```java
public class Test {
    public static void main(String[] args) {
        System.out.println(args[0]);
    }
}
```

#### **Execution Commands and Outputs:**

1. **Command:**
   ```sh
   javac Test.java
   java Test Note Book
   ```
   **Output:**
   ```
   Note
   ```
   **Explanation:**
   - `"Note"` and `"Book"` are treated as separate arguments (`args[0] = "Note"`, `args[1] = "Book"`). The program prints only `args[0]`.

2. **Command:**
   ```sh
   java Test "Note Book"
   ```
   **Output:**
   ```
   Note Book
   ```
   **Explanation:**
   - `"Note Book"` is treated as a single argument (`args[0] = "Note Book"`) due to the double quotes.

---


## **Java Coding Standards**

When writing Java code, it is highly recommended to follow coding standards. The name of each component (class, method, variable, etc.) should reflect its purpose or functionality. The main advantages of this approach are improved **readability** and **maintainability** of the code.

### **Example of Poor Naming**
```java
class A {
    public int m1(int x, int y) {
        return x + y;
    }
}
```

### **Example of Proper Naming**
```java
package com.durgasoft.acjp;

public class Calculator {
    public int add(int number1, int number2) {
        return number1 + number2;
    }
}
```

---

### **Class Naming Conventions**
- Class names should be **nouns**.
- They should start with an **uppercase character**.
- If the name contains multiple words, every inner word should start with an uppercase character (CamelCase).
- **Examples:** `String`, `StringBuffer`, `BigDog`

---

### **Interface Naming Conventions**
- Interface names should be **adjectives**.
- They should start with an **uppercase character**.
- If the name contains multiple words, every inner word should start with an uppercase character (CamelCase).
- **Examples:** `Runnable`, `Comparable`

---

### **Method Naming Conventions**
- Method names should be **verbs** or **verb-noun combinations**.
- They should start with a **lowercase letter**.
- If the name contains multiple words, every inner word should start with an uppercase character (CamelCase).
- **Examples:** `print`, `sleep`, `start`, `getName`, `setSalary`

---

### **Variable Naming Conventions**
- Variable names should be **nouns**.
- They should start with a **lowercase letter**.
- If the name contains multiple words, every inner word should start with an uppercase character (CamelCase).
- **Examples:** `name`, `age`, `mobileNumber`

---

### **Constant Naming Conventions**
- Constant names should be **nouns**.
- They should contain only **uppercase characters**.
- If the name contains multiple words, the words should be separated by an **underscore (`_`)**.
- Constants are typically declared with the `public static final` modifiers.
- **Examples:** `MAX_VALUE`, `MAX_PRIORITY`, `MIN_PRIORITY`, `PI`

---

### **JavaBean Coding Standards**
A **JavaBean** is a simple Java class with private properties, along with public getter and setter methods.

### **Example**
```java
public class StudentBean {
    private String name;

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}
```

- **Note:** Ending a class name with `Bean` is a common convention but not an official requirement.

---

### **Setter Method Standards**
1. Must be a **public method**.
2. Return type must be **void**.
3. Method name must be prefixed with `set`.
4. Must take at least one argument (no-argument setters are not allowed).

---

### **Getter Method Standards**
1. Must be a **public method**.
2. Return type must **not** be void.
3. Method name must be prefixed with `get`.
4. Must not take any arguments.

---

### **Boolean Properties**
- For boolean properties, the getter method can be prefixed with either `get` or `is`.
- The `is` prefix is recommended for boolean properties.


```java
private boolean empty;

public boolean getEmpty() {
    return empty;
}

public boolean isEmpty() {
    return empty;
}
```

---

### **Listener Naming Conventions**

#### **Case 1: Registering a Listener**
- Method names should be prefixed with `add` or `register`.
- **Examples:**
```java
public void addMyActionListener(MyActionListener listener) {
    // Logic to add listener
}

public void registerMyActionListener(MyActionListener listener) {
    // Logic to register listener
}
```

---

#### **Case 2: Unregistering a Listener**
- Method names should be prefixed with `remove`, `unregister`, or `delete`.
- **Examples:**
```java
public void removeMyActionListener(MyActionListener listener) {
    // Logic to remove listener
}

public void unregisterMyActionListener(MyActionListener listener) {
    // Logic to unregister listener
}

public void deleteMyActionListener(MyActionListener listener) {
    // Logic to delete listener
}
```
---