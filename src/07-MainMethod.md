## **Main Method**  

**JVM Checks at Runtime**  
- The compiler does **not** check whether a class contains a `main` method or if it is declared correctly.  
- The **JVM (Java Virtual Machine)** is responsible for verifying and invoking the `main` method at runtime.  
- If the JVM **cannot find** the `main` method, it throws a **runtime exception**:  
```
Exception in thread "main" java.lang.NoSuchMethodError: main
```

2. **Example: Missing `main` Method**  
```java
class Test {
 // No main method
}
```
**Compilation:**  
```
javac Test.java  // Compiles successfully
```
**Execution:**  
```
java Test
```
**Runtime Error:**  
```
Exception in thread "main" java.lang.NoSuchMethodError: main
```

3. **JVM Searches for the Following Method Signature**  
```java
public static void main(String[] args)
```
### **Explanation of `public static void main(String[] args)` in Java**  

1. **`public`**  
- The `main` method must be accessible from anywhere in the program.  
- The JVM (Java Virtual Machine) needs to call this method from outside the class.  

2. **`static`**  
- The JVM can call the `main` method without creating an instance of the class.  
- This ensures that execution starts as soon as the class is loaded.  

3. **`void`**  
- The `main` method does not return any value.  
- The JVM does not expect any output from this method.  

4. **`main(String[] args)`**  
- `"main"` is the predefined method name in Java.  
- The JVM looks for this specific method signature to start execution.  

5. **`String[] args`**  
- Used for command-line arguments.  
- Allows passing input values when executing the program from the terminal.

6. **Strict Method Signature Rules**  
- Any deviation from the standard `main` method signature results in a **runtime exception**:  
```
Exception in thread "main" java.lang.NoSuchMethodError: main
```
- **Example of Invalid `main` Methods:**
```java
static void main(String[] args) // Missing 'public'   
public void main(String[] args) // Missing 'static'   
public static int main(String[] args) // Return type should be 'void'   
public static void main(String args) // Parameter should be 'String[]'   
```

---

### **Accepted Variations in Java `main` Method Syntax**

Even though the syntax of the `main` method in Java is strict, the following changes are acceptable:

1. **Order of Modifiers**  
   - Instead of `public static`, we can use `static public`.  
     ```java
     static public void main(String[] args) { }
     ```

2. **Different Ways to Declare String Array**  
   - The array declaration syntax can vary:  
     ```java
     public static void main(String[] args) { }   // Standard
     public static void main(String []args) { }   // Space before []
     public static void main(String args[]) { }   // Brackets after variable name
     ```

3. **Using Any Valid Java Identifier Instead of `args`**  
   - The argument name can be changed as long as it is a valid identifier:  
     ```java
     public static void main(String[] anyName) { }
     ```

4. **Using Varargs Instead of String Array**  
   - We can replace the `String[]` parameter with varargs:  
     ```java
     public static void main(String... parameters) { }
     ```


---


### **Modifiers Allowed in Java `main` Method**

1. We can declare the `main` method with additional modifiers like `final`, `synchronized`, and `strictfp`.  
2. Example:
   ```java
   class Test {
       static final synchronized strictfp public void main(String... durga) {
           System.out.println("valid main method");
       }
   }
   ```
3. The above declaration is valid because the order of modifiers does not matter, and `main` is still recognizable by the JVM.

---

### **Question 1: Which of the following `main` method declarations are valid?**

1. `public static void main(String args)` → **Invalid** (should be `String[]` or `String...`).  
2. `public static void Main(String[] args)` → **Invalid** (`Main` must be lowercase `main`).  
3. `public void main(String[] args)` → **Invalid** (must be `static`).  
4. `public static int main(String[] args)` → **Invalid** (`main` must return `void`).  
5. `final synchronized strictfp public void main(String[] args)` → **Invalid** (`main` must be `static`).  
6. `final synchronized strictfp public static void main(String[] args)` → **Valid** (modifiers are allowed, and `main` is static).  
7. `public static void main(String... args)` → **Valid** (varargs are allowed).  

---

### **Question 2: In which cases do we get a compile-time error?**

1. `public static void main(String args)` → **No compile-time error**, but **runtime error** (`NoSuchMethodError: main`).  
2. `public static void Main(String[] args)` → **No compile-time error**, but **runtime error** (`NoSuchMethodError: main`).  
3. `public void main(String[] args)` → **No compile-time error**, but **runtime error** (`NoSuchMethodError: main`).  
4. `public static int main(String[] args)` → **Compile-time error** (return type must be `void`).  
5. `final synchronized strictfp public void main(String[] args)` → **Compile-time error** (must be `static`).  
6. `final synchronized strictfp public static void main(String[] args)` → **No compile-time error**, valid method.  
7. `public static void main(String... args)` → **No compile-time error**, valid method.  

> **Conclusion:**  
> - In the last two cases (`final synchronized strictfp public static void main(String[] args)` and `public static void main(String... args)`), **no compile-time error occurs**.  
> - In the remaining cases except for `int` return type and missing `static`, **no compile-time error occurs**, but the JVM throws a **runtime exception (`NoSuchMethodError: main`)** because it cannot find a valid `main` method.  

---

### **Case 1: Overloading the `main` Method**

1. Overloading the `main` method is possible, but the JVM always calls the `main(String[] args)` version.  
2. Other overloaded versions must be called explicitly like normal methods.  
3. Example:
   ```java
   class Test {
       public static void main(String[] args) {
           System.out.println("String[]");
       }

       public static void main(int[] args) {
           System.out.println("int[]");
       }
   }
   ```
4. **Output:**
   ```
   String[]
   ```
5. Even though there is an `int[]` version, the JVM only calls `main(String[] args)`.  

---

### **Case 2: Inheritance and `main` Method Execution**

1. The `main` method follows **inheritance** like any other `static` method.  
2. If the child class does not define its own `main`, it inherits the `main` method from the parent class.  
3. Example:
   ```java
   // P.java
   class P {
       public static void main(String[] args) {
           System.out.println("Parent main");
       }
   }

   // C.java
   class C extends P {
       // No main method in C
   }
   ```
4. **Execution:**
   - Running `java P` → Output: `Parent main`.  
   - Running `java C` → Output: `Parent main`.  

> **Conclusion:** If a child class does not define a `main` method, the parent class `main` method is executed.

---

### **Case 3: Method Hiding Instead of Overriding**

1. `main` method **looks like it can be overridden**, but it actually follows **method hiding**.  
2. When a subclass defines its own `main`, it does **not override** the parent class’s `main`. Instead, it hides it.  
3. Example:
   ```java
   // P.java
   class P {
       public static void main(String[] args) {
           System.out.println("Parent main");
       }
   }

   // C.java
   class C extends P {
       public static void main(String[] args) {
           System.out.println("Child main");
       }
   }
   ```
4. **Execution:**
   - Running `java P` → Output: `Parent main`.  
   - Running `java C` → Output: `Child main`.  

> **Conclusion:**  
> - **Inheritance and overloading** apply to the `main` method.  
> - **Overriding is not applicable** to `static` methods, so method hiding happens instead. 

---

### **Java 1.7 Enhancements with Respect to the `main` Method**

#### **1. Behavior Before Java 1.7**
- If a class does not contain a `main` method, running the program results in a runtime exception.
- The error message in Java 1.6 is `java.lang.NoSuchMethodError: main`, which does not provide much clarity.

#### **2. Behavior After Java 1.7**
- From Java 1.7 onwards, if the `main` method is missing, the program does not throw a runtime exception.
- Instead, it provides a more detailed error message:  
  **"Error: Main method not found in class Test, please declare the main method as public static void main(String[] args)"**.

#### **3. Example: Class Without a `main` Method**
```java
class Test {
}
```
- In Java 1.6:
  - Compilation succeeds.
  - Execution results in `NoSuchMethodError: main`.
- In Java 1.7:
  - Compilation succeeds.
  - Execution results in an error stating that the `main` method is missing.

#### **4. Execution of Static Blocks Before and After Java 1.7**
- Prior to Java 1.7, if a class contained a static block, the static block would execute even if the `main` method was missing.
- From Java 1.7 onwards, static blocks do not execute if the `main` method is missing.

#### **5. Example: Class With Only a Static Block**
```java
class Test {
    static {
        System.out.println("Static Block");
    }
}
```
- In Java 1.6:
  - Compilation succeeds.
  - Execution prints `Static Block`.
- In Java 1.7:
  - Compilation succeeds.
  - Execution results in an error stating that the `main` method is missing.

#### **6. Effect of `System.exit(0)` Inside a Static Block**
- Prior to Java 1.7, if a class contained a static block with `System.exit(0)`, the program would terminate successfully without checking for the `main` method.
- From Java 1.7 onwards, even if `System.exit(0)` is present inside a static block, the program still throws an error if the `main` method is missing.

#### **7. Example: Class With `System.exit(0)` Inside a Static Block**
```java
class Test {
    static {
        System.out.println("Static Block");
        System.exit(0);
    }
}
```
- In Java 1.6:
  - Compilation succeeds.
  - Execution prints `Static Block` and terminates normally.
- In Java 1.7:
  - Compilation succeeds.
  - Execution results in an error stating that the `main` method is missing.

#### **8. Behavior When `main` Method is Present Along With a Static Block**
- If a class contains both a static block and a `main` method, the static block executes first, followed by the `main` method.

#### **9. Example: Class With Both Static Block and `main` Method**
```java
class Test {
    static {
        System.out.println("Static Block");
    }

    public static void main(String[] args) {
        System.out.println("Main Method");
    }
}
```
- In Java 1.6:
  - Compilation succeeds.
  - Execution prints `Static Block` followed by `Main Method`.
- In Java 1.7:
  - Compilation succeeds.
  - Execution prints `Static Block` followed by `Main Method`.

#### **10. Execution Flow in Java 1.6**
1. The Java Virtual Machine (JVM) identifies static members.
2. Static variable assignments and static blocks execute.
3. The JVM checks for the presence of the `main` method.
4. If the `main` method is present, it executes.
5. If the `main` method is missing, the program throws a runtime exception: `NoSuchMethodError: main`.

#### **11. Execution Flow in Java 1.7**
1. The JVM first checks whether the `main` method is present.
2. If the `main` method is not found, it throws an error stating that the `main` method is missing.
3. If the `main` method is present, the JVM identifies static members.
4. Static variable assignments and static blocks execute.
5. The `main` method executes.

#### **12. Printing Output Without a `main` Method**
- Before Java 1.7, it was possible to print output to the console without a `main` method by using a static block.
- From Java 1.7 onwards, it is no longer possible to print anything to the console without a `main` method.
