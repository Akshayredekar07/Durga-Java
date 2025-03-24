## **Assignment Operators in Java**  

Assignment operators in Java are used to assign values to variables. They can be classified into three types:  

1. **Simple Assignment**  
2. **Chained Assignment**  
3. **Compound Assignment**  

---

### **1. Simple Assignment**  
- A simple assignment operator assigns a value to a variable.  
- Example:  

  ```java
  int x = 10;
  ```
  
---

### **2. Chained Assignment**  
- Chained assignment allows assigning the same value to multiple variables in a single statement.  
- Example:  

  ```java
  int a, b, c, d;
  a = b = c = d = 20;
  System.out.println(a + "..." + b + "..." + c + "..." + d);
  ```
  
  **Output:**  
  ```
  20...20...20...20
  ```

#### **Chained Assignment at Declaration - Not Allowed**  
- Java does **not** allow chained assignment directly at the time of declaration.  
- Example:  

  ```java
  int a = b = c = d = 20; 
  // Compilation Error: cannot find symbol
  // Symbol: variable b
  // Location: class Test
  ```
  
**Correct Alternative:**  
- Declare variables separately before assigning values.  

  ```java
  int b, c, d;
  int a = b = c = d = 20;
  ```

---

### **3. Compound Assignment**  
- Compound assignment operators combine an assignment operator with an arithmetic or bitwise operation.  
- Example:  

  ```java
  int a = 10;
  a += 20;  // Equivalent to: a = a + 20;
  System.out.println(a);  // Output: 30
  ```

#### **List of Compound Assignment Operators**
| Operator | Equivalent To |
|----------|--------------|
| `+=` | `a = a + b` |
| `-=` | `a = a - b` |
| `*=` | `a = a * b` |
| `/=` | `a = a / b` |
| `%=` | `a = a % b` |
| `&=` | `a = a & b` |
| `|=` | `a = a | b` |
| `^=` | `a = a ^ b` |
| `<<=` | `a = a << b` |
| `>>=` | `a = a >> b` |
| `>>>=` | `a = a >>> b` |

---

### **Bitwise Shift Example**
- The right shift operator (`>>`) divides the number by `2^n`, where `n` is the shift count.  

  ```java
  int num = 20;
  System.out.println(num >> 2);  // Output: 5
  ```

---

### **Automatic Type Casting in Compound Assignment**  
- When using a compound assignment operator, implicit type casting happens automatically.  

#### **Example 1: Without Compound Assignment (Error)**
```java
byte b = 10;
b = b + 1;  
// Compilation Error: possible lossy conversion from int to byte
```
**Reason:**  
- `b + 1` results in an `int`, but `b` is a `byte`, so explicit type casting is required.  

#### **Example 2: Using Compound Assignment (Valid)**
```java
byte b = 10;
b++;  // Works fine because it includes implicit type casting
System.out.println(b);  
```

Equivalent to:
```java
byte b = 10;
b = (byte)(b + 1);  // Explicit type casting
System.out.println(b);
```

---

### **Overflow in Byte Type**
- If an operation results in a value beyond the byte range (-128 to 127), it wraps around.  

#### **Example: Byte Overflow**
```java
byte b = 127;
b += 3;  // Equivalent to: b = (byte)(127 + 3);
System.out.println(b);  // Output: -126
```

**Explanation:**  
- `127 + 3 = 130`
- In binary: `130` is `10000010`  
- Since `byte` is 8-bit, it overflows and results in `-126`.  

---
### Example

- **Code**:
  ```java
  int a, b, c, d;
  a = b = c = d = 20;
  a += b -= c *= d /= 2;
  System.out.println(a + " " + b + " " + c + " " + d);
  // Outputs: -160 -180 200 10
  ```

- **Evaluation (Right to Left)**:
  - `d /= 2`: `d = 20 / 2 = 10`.
  - `c *= d`: `c = 20 * 10 = 200`.
  - `b -= c`: `b = 20 - 200 = -180`.
  - `a += b`: `a = 20 + (-180) = -160`.

- **Result**:
  - `a = -160`, `b = -180`, `c = 200`, `d = 10`.
---


## 🚀 **1. Swap Two Variables Without Using Third Variable**
**Question:** Swap two integers `a` and `b` without using a third variable.

✅ **Solution:**
```java
public class Main {
    public static void main(String[] args) {
        int a = 5, b = 10;
        
        a = a + b;  // a = 15
        b = a - b;  // b = 5
        a = a - b;  // a = 10
        
        System.out.println("After Swap: a = " + a + ", b = " + b);
    }
}
```
📝 **Explanation:**  
- `a` becomes sum of both numbers.
- `b` gets original value of `a`.
- `a` gets original value of `b`.

---

## 🎯 **2. Swap Using XOR (Bitwise Operator)**
**Question:** Swap two numbers using XOR.

✅ **Solution:**
```java
public class Main {
    public static void main(String[] args) {
        int a = 5, b = 10;

        a ^= b;  // a = a ^ b
        b ^= a;  // b = b ^ a
        a ^= b;  // a = a ^ b

        System.out.println("After Swap: a = " + a + ", b = " + b);
    }
}
```
📝 **Explanation:**  
- XOR helps swap bits without extra space.

---

## 🧠 **3. Detect Even or Odd Without Using Modulus Operator**
**Question:** Write a program to determine if a number is even or odd without using `%` operator.

✅ **Solution:**
```java
public class Main {
    public static void main(String[] args) {
        int num = 7;
        
        if ((num & 1) == 0) {
            System.out.println(num + " is Even");
        } else {
            System.out.println(num + " is Odd");
        }
    }
}
```
📝 **Explanation:**  
- `num & 1` checks the least significant bit.  
- If the result is `0`, the number is even.  
- If the result is `1`, the number is odd.

---

## 📚 **4. Divide a Number by 2 Without Using Division**
**Question:** Divide an integer by 2 without using division or modulus operator.

✅ **Solution:**
```java
public class Main {
    public static void main(String[] args) {
        int num = 20;
        
        int result = num >> 1;  // Right shift by 1 is equivalent to dividing by 2
        System.out.println("Result after division by 2: " + result);
    }
}
```
📝 **Explanation:**  
- Right shifting a number (`num >> 1`) divides it by 2.

---

## 🔥 **5. Multiply by 2 Without Using Multiplication Operator**
**Question:** Multiply a number by 2 without using `*` operator.

✅ **Solution:**
```java
public class Main {
    public static void main(String[] args) {
        int num = 7;
        
        int result = num << 1;  // Left shift by 1 is equivalent to multiplying by 2
        System.out.println("Result after multiplying by 2: " + result);
    }
}
```
📝 **Explanation:**  
- Left shifting a number (`num << 1`) multiplies it by 2.

---

## 📢 **6. Check if Number is Power of 2**
**Question:** Check if a number is a power of 2.

✅ **Solution:**
```java
public class Main {
    public static boolean isPowerOfTwo(int n) {
        return (n > 0) && ((n & (n - 1)) == 0);
    }
    
    public static void main(String[] args) {
        int num = 16;
        
        if (isPowerOfTwo(num)) {
            System.out.println(num + " is a power of 2.");
        } else {
            System.out.println(num + " is not a power of 2.");
        }
    }
}
```
📝 **Explanation:**  
- `n & (n - 1)` equals zero only when `n` is a power of 2.

---

## 🤯 **7. Swap Two Bits in a Number**
**Question:** Swap two bits at given positions in an integer.

✅ **Solution:**
```java
public class Main {
    public static int swapBits(int n, int p1, int p2) {
        // Get bits at positions p1 and p2
        int bit1 = (n >> p1) & 1;
        int bit2 = (n >> p2) & 1;
        
        if (bit1 != bit2) {
            n ^= (1 << p1);
            n ^= (1 << p2);
        }
        return n;
    }
    
    public static void main(String[] args) {
        int n = 28;  // 11100 in binary
        int p1 = 1, p2 = 3;
        
        int result = swapBits(n, p1, p2);
        System.out.println("Number after swapping bits: " + result);
    }
}
```
📝 **Explanation:**  
- XORing the bits changes their positions only if they are different.

---

## 🧑‍💻 **8. Add Two Numbers Without Using `+` Operator**
**Question:** Add two integers without using `+` or `-` operator.

✅ **Solution:**
```java
public class Main {
    public static int add(int a, int b) {
        while (b != 0) {
            int carry = a & b;  // Carry calculation
            a = a ^ b;  // Sum of bits without carry
            b = carry << 1;  // Carry propagated to next position
        }
        return a;
    }
    
    public static void main(String[] args) {
        int num1 = 5, num2 = 7;
        
        System.out.println("Sum: " + add(num1, num2));
    }
}
```
📝 **Explanation:**  
- `&` finds carry bits.  
- `^` adds without carry.

---

## 🧩 **9. Find Missing Number in Array (1 to n)**
**Question:** Find the missing number in an array of size `n-1` containing numbers from `1` to `n`.

✅ **Solution:**
```java
public class Main {
    public static int findMissing(int[] arr, int n) {
        int total = n * (n + 1) / 2;  // Sum of first n numbers
        int sum = 0;
        
        for (int num : arr) {
            sum += num;
        }
        
        return total - sum;
    }
    
    public static void main(String[] args) {
        int[] arr = {1, 2, 4, 5, 6};
        int n = 6;
        
        System.out.println("Missing number: " + findMissing(arr, n));
    }
}
```
📝 **Explanation:**  
- Sum of first `n` numbers minus the sum of array elements gives the missing number.

---

## 🕵️ **10. Reverse Bits of a Number**
**Question:** Reverse the bits of an integer.

✅ **Solution:**
```java
public class Main {
    public static int reverseBits(int n) {
        int result = 0;
        
        for (int i = 0; i < 32; i++) {
            result <<= 1;  // Shift result left by 1
            result |= (n & 1);  // Add least significant bit of n to result
            n >>= 1;  // Shift n right by 1
        }
        return result;
    }
    
    public static void main(String[] args) {
        int num = 5;  // 101 in binary
        System.out.println("Reversed bits: " + reverseBits(num));
    }
}
```
📝 **Explanation:**  
- Shift bits one by one and add to result.

---



### Explanation of the Ternary Operator in Java

The ternary operator in Java, also known as the conditional operator, is a concise way to perform a conditional check and return one of two values based on the result. It has the syntax:

```
condition ? valueIfTrue : valueIfFalse
```

- **How it works**:
  - The `condition` is evaluated (must return a boolean).
  - If `condition` is `true`, `valueIfTrue` is returned.
  - If `condition` is `false`, `valueIfFalse` is returned.

### One Sentence (Without Example)
The ternary operator in Java evaluates a boolean condition and returns one of two values based on whether the condition is true or false, using the syntax `condition ? valueIfTrue : valueIfFalse`.


### **Ternary Operator in Java**

The **ternary operator** (`? :`) in Java is a shorthand for `if-else` statements. It is also known as the **conditional operator** and follows the syntax:

```java
condition ? expression1 : expression2;
```

- If `condition` is **true**, `expression1` is evaluated.
- If `condition` is **false**, `expression2` is evaluated.

---

### **Examples and Edge Cases**

#### **1. Basic Usage**
```java
int a = 10, b = 20;
int min = (a < b) ? a : b; // min is assigned 10
```
**Explanation:** Since `a < b` is **true**, `min` gets the value of `a` (which is 10).

---

#### **2. Using with Methods**
```java
public class TernaryExample {
    static int max(int x, int y) {
        return (x > y) ? x : y;
    }
    
    public static void main(String[] args) {
        System.out.println(max(10, 20)); // Output: 20
    }
}
```
**Explanation:** The method `max()` returns the larger of the two numbers using the ternary operator.

---

#### **3. Nested Ternary Operators**
```java
int num = -5;
String result = (num > 0) ? "Positive" : (num < 0) ? "Negative" : "Zero";
System.out.println(result); // Output: Negative
```
**Explanation:** If `num > 0`, it returns `"Positive"`, otherwise, it checks `num < 0` and returns `"Negative"`, otherwise `"Zero"`.

---

### **Tricky Edge Cases**
#### **4. Mixing Data Types**
```java
int a = 5;
double b = 2.5;
double result = (a > b) ? a : b; // Works fine, implicit casting to double
System.out.println(result); // Output: 5.0
```
**Explanation:** Since one operand (`b`) is `double`, `a` is automatically promoted to `double`.

---

#### **5. Using Ternary with Side Effects**
```java
int a = 5;
int b = 10;
int max = (a > b) ? a++ : b--; // b is decremented
System.out.println("a = " + a + ", b = " + b); // a = 5, b = 9
```
**Explanation:** Since `a > b` is **false**, `b--` executes, reducing `b` to 9.

---

#### **6. Returning from a Ternary Expression**
```java
public class Test {
    static void check(int x) {
        System.out.println(x > 0 ? "Positive" : "Non-positive");
    }

    public static void main(String[] args) {
        check(-2); // Output: Non-positive
    }
}
```
**Explanation:** The ternary operator can be used inside `System.out.println()` directly.

---

## **Operators precedence**

- In Java, we have only **operator precedence**, but not operand precedence.
- Before applying any operator, all operands will be evaluated from **left to right**.

### 1. Operator Precedence in Java
- Java follows a strict **operator precedence** rules to determine the order in which operators are applied in an expression.
- For example, in the expression `a + b * c`, the multiplication (`*`) has higher precedence than addition (`+`), so `b * c` is evaluated first, and then the result is added to `a`.
- Java does **not** have operand precedence, meaning the operands themselves (e.g., `a`, `b`, `c`) do not have an inherent priority based on their position or type. The precedence is determined solely by the operators.

#### Example of Operator Precedence:
```java
int a = 2, b = 3, c = 4;
int result = a + b * c; // Multiplication (*) has higher precedence than addition (+)
System.out.println(result); // Output: 14 (because 3 * 4 = 12, then 2 + 12 = 14)
```

### 2. Operand Evaluation Order (Left to Right)
- In Java, before any operator is applied, all operands in an expression are evaluated from **left to right**.
- This means that if an operand involves a method call, a variable, or a sub-expression, Java will evaluate each operand in the order they appear (from left to right) before applying the operators according to their precedence.

#### Example of Operand Evaluation:
Consider the following code:
```java
class Test {
    public static void main(String[] args) {
        System.out.println(m1(2) * m1(3) / m1(1) + m1(2) * m1(3) * m1(6));
    }

    public static int m1(int i) {
        System.out.println(i);
        return i;
    }
}
```

**Expression:** `m1(2) * m1(3) / m1(1) + m1(2) * m1(3) * m1(6)`

- **Operand Evaluation (Left to Right):**
  - Java evaluates each operand (i.e., each `m1` call) from left to right before applying the operators.
  - First part: `m1(2) * m1(3) / m1(1)`
    - Evaluates `m1(2)` → prints `2`, returns `2`.
    - Evaluates `m1(3)` → prints `3`, returns `3`.
    - Evaluates `m1(1)` → prints `1`, returns `1`.
  - Second part: `m1(2) * m1(3) * m1(6)`
    - Evaluates `m1(2)` → prints `2`, returns `2`.
    - Evaluates `m1(3)` → prints `3`, returns `3`.
    - Evaluates `m1(6)` → prints `6`, returns `6`.

- **Output from Operand Evaluation:**
  ```
  2
  3
  1
  2
  3
  6
  ```

- **Apply Operators (Using Precedence):**
  - After evaluating all operands, Java applies the operators based on their precedence.
  - Multiplication (`*`) and division (`/`) have higher precedence than addition (`+`), and they are evaluated from left to right.
  - First part: `2 * 3 / 1 = 6 / 1 = 6`
  - Second part: `2 * 3 * 6 = 6 * 6 = 36`
  - Combine: `6 + 36 = 42`

- **Final Output:**
  ```
  2
  3
  1
  2
  3
  6
  42
  ```
---

1. **Unary Operators:**  
   - `[ ]` (array indexing)  
   - `x++` (post-increment)  
   - `x--` (post-decrement)  
   - `++x` (pre-increment)  
   - `--x` (pre-decrement)  
   - `~` (bitwise NOT)  
   - `!` (logical NOT)  
   - `new` (object creation)  
   - `<type>` (type casting)

2. **Arithmetic Operators:**  
   - `*` (multiplication)  
   - `/` (division)  
   - `%` (modulus)  
   - `+` (addition)  
   - `-` (subtraction)

3. **Shift Operators:**  
   - `>>` (right shift)  
   - `>>>` (unsigned right shift)  
   - `<<` (left shift)

4. **Comparison Operators:**  
   - `<` (less than)  
   - `<=` (less than or equal to)  
   - `>` (greater than)  
   - `>=` (greater than or equal to)  
   - `instanceof` (type comparison)

5. **Equality Operators:**  
   - `==` (equal to)  
   - `!=` (not equal to)

6. **Bitwise Operators:**  
   - `&` (bitwise AND)  
   - `^` (bitwise XOR)  
   - `|` (bitwise OR)

7. **Short Circuit Operators:**  
   - `&&` (logical AND, short-circuit)  
   - `||` (logical OR, short-circuit)

8. **Conditional Operator:**  
   - `?:` (ternary operator, e.g., `condition ? value1 : value2`)

9. **Assignment Operators:**  
   - `=` (simple assignment)  
   - `+=` (add and assign)  
   - `-=` (subtract and assign)  
   - `*=` (multiply and assign)  
   - `/=`, `%=`, `&=`, `|=`, `^=`, `<<=`, `>>=`, `>>>=`

---


### 1. **Bitwise NOT (`~`)**
- **What it does:** The `~` operator is a **unary bitwise operator** that inverts all the bits of its operand. It works on integer types (`int`, `long`, `short`, `byte`).
- **How it works:** For each bit in the number, `~` flips it:
  - `0` becomes `1`.
  - `1` becomes `0`.
- **Operand type:** Integer types (e.g., `int`, `long`). The result is also an integer.
- **Effect on the number:** For a number `x`, the `~x` operation is equivalent to `-(x + 1)` due to how numbers are represented in two's complement form in Java.

#### Example of `~`:
Let’s take the number `5` (an `int` in Java):
- Binary representation of `5` (32-bit `int`):  
  `00000000 00000000 00000000 00000101`
- Apply `~5`: Flip all bits:  
  `11111111 11111111 11111111 11111010`
- This binary number is the two's complement representation of `-6`.  
  (To understand why: `~5` = `-(5 + 1)` = `-6`.)

**Code Example:**
```java
int x = 5;
System.out.println(~x); // Output: -6
```

- Another example with `0`:  
  - `0` in binary: `00000000 00000000 00000000 00000000`
  - `~0`: `11111111 11111111 11111111 11111111`, which is `-1`.  
  So, `~0` = `-1`.

---

### 2. **Logical NOT (`!`)**
- **What it does:** The `!` operator is a **unary logical operator** that negates a boolean value. It works on boolean expressions or values.
- **How it works:** It flips the truth value:
  - `true` becomes `false`.
  - `false` becomes `true`.
- **Operand type:** `boolean`. The result is also a `boolean`.
- **Use case:** Typically used in conditional statements or logical expressions to invert a condition.

#### Example of `!`:
- If a variable `flag` is `true`, then `!flag` is `false`.
- If `flag` is `false`, then `!flag` is `true`.

**Code Example:**
```java
boolean flag = true;
System.out.println(!flag); // Output: false

flag = false;
System.out.println(!flag); // Output: true
```

- Another example with a condition:  
  ```java
  int x = 10;
  boolean isPositive = x > 0; // true
  System.out.println(!isPositive); // Output: false
  ```

---

### Key Differences Between `~` and `!`

| **Aspect**            | **Bitwise NOT (`~`)**                          | **Logical NOT (`!`)**                          |
|-----------------------|-----------------------------------------------|-----------------------------------------------|
| **Type of Operator**  | Bitwise (operates on bits)                   | Logical (operates on truth values)            |
| **Operand Type**      | Integer types (`int`, `long`, `short`, `byte`) | `boolean`                                     |
| **Result Type**       | Same as the operand (e.g., `int`)            | `boolean`                                     |
| **Operation**         | Inverts all bits (0 → 1, 1 → 0)              | Inverts the boolean value (`true` → `false`, `false` → `true`) |
| **Use Case**          | Manipulating bits in numbers (e.g., in low-level programming) | Controlling logic in conditionals (e.g., `if` statements) |
| **Example**           | `~5` = `-6` (flips bits of 5)                | `!true` = `false` (negates the boolean)       |

---

### Common Mistake to Avoid
- **Using `~` on a boolean:** This will cause a compilation error in Java because `~` is not defined for `boolean` types.
  ```java
  boolean b = true;
  System.out.println(~b); // Compilation error: "operator ~ cannot be applied to boolean"
  ```
- **Using `!` on an integer:** Similarly, this will cause a compilation error because `!` is not defined for integer types.
  ```java
  int x = 5;
  System.out.println(!x); // Compilation error: "operator ! cannot be applied to int"
  ```

---

### Practical Use Cases
- **`~` (Bitwise NOT):**
  - Used in low-level programming, such as bit manipulation, flags, or masks.
  - Example: Inverting a bitmask to select all bits except certain ones.
    ```java
    int mask = 5; // 00000101
    int invertedMask = ~mask; // 11111010
    ```

- **`!` (Logical NOT):**
  - Used in control flow to negate conditions.
  - Example: Checking if a condition is not true.
    ```java
    if (!(x > 0)) {
        System.out.println("x is not positive");
    }
    ```

---

The `~` (bitwise NOT) operator inverts all bits of an integer, while the `!` (logical NOT) operator inverts a boolean value. They differ in their operand types (`~` for integers, `!` for booleans), their operation (bit flipping vs. logical negation), and their use cases (bit manipulation vs. logical control).

---


```java
class Test {
    public static void main(String[] args) {
        int a = 5, b = 3, c = 2;
        boolean x = true, y = false;
        
        System.out.println((a + b * c) > (a - b / c) ^ (a & b) != 0 ? !(x && y) || (c < b) : a * b + c);
    }
}
```

```java
class Test {
    public static void main(String[] args) {
        System.out.println((m1(1) + m1(2) * m1(3)) > (m1(4) / m1(5)) && !((m1(6) & m1(7)) == 0) || m1(8) < m1(9));
    }

    public static int m1(int i) {
        System.out.println(i);
        return i;
    }
}
```