## **Content**

1. Increment and Decrement Operators
2. Arithmetic Operators
3. String Concatenation Operator
4. Relational Operators
5. Equality Operators
6. instanceof Operator
7. Bitwise Operators
8. Short Circuit Operators
9. Type Cast Operator
10. Assignment Operators
11. Conditional Operator
12. new Operator
13. [] Operator
14. Operator Precedence
15. Evaluation Order of Operands
16. new Vs newInstance()
17. instanceof Vs isInstance()
18. ClassNotFoundException Vs NoClassDefFoundError

---

## **Increment and Decrement Operators in Java**  

### **Increment Operators**  
- **Pre-Increment (`++x`)**: Increments the value of `x` **before** using it.  
  - Example: `y = ++x;`  
- **Post-Increment (`x++`)**: Uses the value of `x` **first**, then increments it.  
  - Example: `y = x++;`  

### **Decrement Operators**  
- **Pre-Decrement (`--x`)**: Decrements the value of `x` **before** using it.  
  - Example: `y = --x;`  
- **Post-Decrement (`x--`)**: Uses the value of `x` **first**, then decrements it.  
  - Example: `y = x--;`  

### **Expression Evaluation Table**  
| Expression | Initial `x` | `y` Value | Final `x` |  
|------------|------------|-----------|-----------|  
| `y = ++x;` | 10         | 11        | 11        |  
| `y = x++;` | 10         | 10        | 11        |  
| `y = --x;` | 10         | 9         | 9         |  
| `y = x--;` | 10         | 10        | 9         |  

---

## **Rules and Restrictions**  

### **1. Operators Can Only Be Applied to Variables**  
- The increment (`++`) and decrement (`--`) operators **cannot** be applied to constant values.  
- Trying to apply them to constants results in a **compile-time error**.  

#### **Valid Example:**  
```java
int x = 10;  
int y = ++x;  
System.out.println(y); // Output: 11  
```

#### **Invalid Example:**  
```java
int y = ++10; // Compilation Error  
System.out.println(y);  
```
**Error:**  
```
CE: Unexpected type  
Found: Value  
Required: Variable  
```

---

### **2. Nesting of Increment/Decrement Operators is Not Allowed**  
- You **cannot** nest increment or decrement operators.  

#### **Invalid Example:**  
```java
int x = 10;  
int y = ++(++x); // Compilation Error  
System.out.println(y);  
```
**Error:**  
```
CE: Unexpected type  
Required: Variable  
Found: Value  
```

---

### **3. Increment/Decrement Cannot Be Applied to `final` Variables**  
- A `final` variable **cannot** be modified after initialization.  
- Using `++` or `--` on a `final` variable results in a **compile-time error**.  

#### **Invalid Example:**  
```java
final int x = 10;  
x++; // Compilation Error  
System.out.println(x);  
```
**Error:**  
```
CE: Cannot assign a value to final variable x  
```

---

### **4. Applicability to Primitive Types**  
- **The `++` and `--` operators can be applied to all primitive types except `boolean`.**  

#### **Valid Examples:**  
```java
int x = 10;  
char ch = 'a';  
double d = 10.5;  

x++;        // x becomes 11  
ch++;       // ch becomes 'b'  
d++;        // d becomes 11.5  

System.out.println(x);  // 11  
System.out.println(ch); // b  
System.out.println(d);  // 11.5  
```

#### **Invalid Example (Boolean):**  
```java
boolean b = true;  
b++; // Compilation Error  
System.out.println(b);  
```
**Error:**  
```
CE: Bad operand type boolean for unary operator '++'  
```

---

## **Difference Between `b + 1` and `b++`**  

### **1. Arithmetic Operations (`b + 1`)**  
- When using an arithmetic operation (`+`), the result type is **max(int, type of operand1, type of operand2)**.  
- Since `b + 1` results in an `int`, an explicit type cast is required for smaller data types like `byte`.  

#### **Invalid Example:**  
```java
byte b = 10;  
b = b + 1; // Compilation Error  
System.out.println(b);  
```
**Error:**  
```
CE: Possible loss of precision  
Found: int  
Required: byte  
```

#### **Fix with Explicit Casting:**  
```java
byte b = 10;  
b = (byte) (b + 1);  
System.out.println(b); // Output: 11  
```

---

### **2. Auto Type Casting in `b++`**  
- The `++` operator performs an **implicit type cast**, so no explicit casting is required.  

#### **Valid Example:**  
```java
byte b = 10;  
b++;  
System.out.println(b); // Output: 11  
```

#### **Equivalent to:**  
```java
byte b = 10;  
b = (byte) (b + 1);  
System.out.println(b); // Output: 11  
```

---

## **Example Program**  
```java
class Test {  
    public static void main(String[] args) {  
        byte a = 10;  
        byte b = 20;  
        byte c = (byte) (a + b);  
        System.out.println(c); // Output: 30  
    }  
}  
```

