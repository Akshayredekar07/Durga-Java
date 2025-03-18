## **Var-Args Methods**  

### **Introduction**  
Before Java 1.5, methods could not accept a variable number of arguments. If the number of arguments changed, developers had to create multiple overloaded methods, leading to:  
- Increased code length  
- Reduced readability  

To address this, Java 1.5 introduced **var-args (variable arguments) methods**, allowing methods to accept an arbitrary number of arguments.

#### **Syntax of Var-Args Methods**  
A var-args method is declared using three dots (`...`) after the parameter type:  

```java
void methodName(int... x) {  
    // Method body  
}
```
- The method can be called with any number of arguments (including zero).  

##### **Example Usage**  
```java
m1(10, 20);  
m1(10, 20, 30);  
m1(10, 20, 30, 40);  
m1(10, 20, 30, 40, 50);
```

---

### **Without Using Var-Args (Before Java 1.5)**  

Before Java 1.5, separate methods were required for different argument counts.  

```java
class Test {
    static void sum(int a, int b) {
        System.out.println("Sum: " + (a + b));
    }

    static void sum(int a, int b, int c) {
        System.out.println("Sum: " + (a + b + c));
    }

    static void sum(int a, int b, int c, int d) {
        System.out.println("Sum: " + (a + b + c + d));
    }

    public static void main(String[] args) {
        sum(10, 20);
        sum(10, 20, 30);
        sum(10, 20, 30, 40);
    }
}
```

##### **Output:**  
```
Sum: 30  
Sum: 60  
Sum: 100  
```
**Problems:**  
- More lines of code  
- Poor maintainability  
- Code duplication  

---

### **Using Var-Args (After Java 1.5)**  

Var-args solve this issue by allowing a single method to handle multiple arguments dynamically.

#### **Example Using Var-Args**
```java
class Test {
    static void sum(int... numbers) {
        int total = 0;
        for (int num : numbers) {
            total += num;
        }
        System.out.println("Sum: " + total);
    }

    public static void main(String[] args) {
        sum(10, 20);
        sum(10, 20, 30);
        sum(10, 20, 30, 40);
        sum(10, 20, 30, 40, 50);
    }
}
```

##### **Output:**  
```
Sum: 30  
Sum: 60  
Sum: 100  
Sum: 150  
```

**Advantages of Var-Args:**  
✔ **Shorter and cleaner code**  
✔ **Better readability and maintainability**  
✔ **No need for method overloading**  

---

## **Var-Args Method Rules and Examples**  

#### **Case 1: Valid and Invalid Var-Args Method Declarations**  
Which of the following are valid var-args method declarations?  

| Method Declaration | Valid/Invalid |
|--------------------|--------------|
| `m1(int... x)`    |  Valid |
| `m1(int ...x)`    |  Valid |
| `m1(int...x)`     |  Valid |
| `m1(int x...)`    |  Invalid (Ellipsis `...` must be after type) |
| `m1(int. ..x)`    |  Invalid (Wrong spacing in `...`) |
| `m1(int .x..)`    |  Invalid (Ellipsis must be together as `...`) |

---

#### **Case 2: Mixing Var-Args with Normal Parameters**  
- We can mix var-args parameters with normal parameters.  
- Examples:  

```java
m1(int x, int... y); 
m1(String s, double... y);
```

---

#### **Case 3: Var-Args Must Be the Last Parameter**  
- If we mix a normal parameter with a var-args parameter, the var-args parameter **must** be the last parameter.  

| Method Declaration | Valid/Invalid |
|--------------------|--------------|
| `m1(double... d, String s)` |  Invalid (Var-args must be last) |
| `m1(char ch, String... s)`  |  Valid |

---

#### **Case 4: Only One Var-Args Parameter Allowed in a Method**  
- Inside a var-args method, we can take only one var-args parameter.  
- We **cannot** have multiple var-args parameters.  

```java
m1(int... x, double... d);  //  Invalid
```

---

#### **Case 5: Cannot Declare Var-Args and 1D Array Method Together**  
- A class **cannot** have a var-args method and a corresponding 1D array method simultaneously; otherwise, we get a **compile-time error**.  

```java
class Test {
    // Compilation Error: Ambiguity
    public void m1(int... x) {
        System.out.println("int...");
    }

    public void m1(int[] x) {
        System.out.println("int[]");
    }
}
```

---

#### **Case 6: Var-Args Have the Lowest Priority**  
- If another method matches the parameters exactly, that method is chosen over the var-args method.  
- The var-args method is **like the default case** in a `switch` statement.  

```java
class Test {
    public static void m1(int... x) {
        System.out.println("Var-Arg Method");
    }

    public static void m1(int x) {
        System.out.println("General Method");
    }

    public static void main(String[] args) {
        m1();         // Calls m1(int... x) → Var-Arg Method
        m1(10, 20);   // Calls m1(int... x) → Var-Arg Method
        m1(10);       // Calls m1(int x) → General Method
    }
}
```

##### **Output:**  
```
Var-Arg Method  
Var-Arg Method  
General Method  
```

---

### **Equivalence Between Var-Args and 1D Arrays**  
- Wherever a **1D array** is used, it can be **replaced** with a var-args parameter:  

```java
m1(int[] x)  ≡  m1(int... x)
main(String[] args)  ≡  main(String... args)
```

| Method Type | Example Calls |
|------------|--------------|
| `m1(int[] x)` | `m1(new int[]{10})`  <br> `m1(new int[]{10, 20})`  <br> `m1(new int[]{10, 20, 30})`  |
| `m1(int... x)` | `m1();`  <br> `m1(0);`  <br> `m1(1);`  <br> `m1(1, 2);`  |

However, **we cannot replace a var-args parameter with a 1D array** directly:  

```java
m1(int... x) == m1(int[] x)  //  Not Valid
```

| `m1(int... x)` Calls | `m1(int[] x)` Equivalent |
|----------------------|-------------------------|
| `m1();`  Invalid  | `X` |
| `m1(10);`  Invalid | `X` |
| `m1(10, 20, 30);`  Invalid | `X` |
| `m1(new int[]{10, 20});`  Valid |  |

---

### **Multidimensional Arrays and Var-Args**  
- If we pass an array to a var-args parameter, it behaves like a **1D array**.  
- Example Equivalences:  

| Var-Args Parameter | Becomes |
|--------------------|---------|
| `m1(int... x)` | `int[] x` |
| `m1(String... x)` | `String[] x` |
| `m1(int[]... x)` | `int[][] x` |
| `m1(int[][]... x)` | `int[][][] x` |

#### **Example of Passing Multiple 1D Arrays to a Var-Args Method**  

```java
class Test {
    public static void main(String[] args) {
        int[] a = {10, 20, 30};
        int[] b = {40, 50, 60};
        m1(a, b);
    }

    public static void m1(int[]... x) {
        for (int[] x1 : x) {
            System.out.println(x1[0]);
        }
    }
}
```

##### **Output:**  
```
10  
40  
```

---

| Rule | Explanation |
|------|------------|
| **Var-Args Syntax** | Declared using `int... x` |
| **Ellipsis Position** | Must be after type (`int... x` , `int x...` ) |
| **Mixing Normal & Var-Args** | Allowed, but var-args must be **last** parameter |
| **Multiple Var-Args** | **Not allowed** in a single method (`m1(int... x, double... y)` ) |
| **Var-Args vs 1D Arrays** | **Cannot** have both in the same class (`m1(int... x)` and `m1(int[] x)`) |
| **Method Priority** | Var-args have **lowest priority** (only used if no exact match) |
| **Var-Args as Arrays** | `m1(int... x)` is equivalent to `int[] x` |
| **Multidimensional Var-Args** | `m1(int[]... x)` is equivalent to `int[][] x` |

---
