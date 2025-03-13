
## **Arrays**

An array is an indexed collection of a fixed number of homogeneous data elements.

#### **Advantages of Arrays:**
- We can store multiple values using a single variable, which improves code readability.

#### **Disadvantages of Arrays:**
- Arrays have a fixed size. Once created, the size cannot be increased or decreased based on requirements.
- Since arrays require a predefined size, it may not always be feasible to determine the required size in advance.

---

### **Array Declaration**

#### **One-Dimensional Array Declarations:**
```java
int[] x;  // Recommended for better readability: variable name is clearly separated from type.
int []x;  
int x[];
```

**Incorrect Declaration:**
```java
int[6] x;  // Not possible. Specifying the array size at declaration results in a compile-time error.
```

---

### **Two-Dimensional Array Declarations:**
```java
int[] x;
int[][] x;
int x[][];
int[] x[];
int[][] x;
```

**Valid Declarations:**
```java
int[] a, b;  // Both 'a' and 'b' are one-dimensional arrays.
int[] a[], b;  // 'a' is a two-dimensional array, but 'b' is a one-dimensional array.
int[] a[], b[];  // Both 'a' and 'b' are two-dimensional arrays.
int[][] a, b;  // Both 'a' and 'b' are two-dimensional arrays.
int[][] a, b[];  // 'a' is a two-dimensional array, but 'b' is a three-dimensional array.
```

**Incorrect Declaration:**
```java
int[][] a, []b[];  // Invalid syntax, results in a compile-time error.
int []a []b []c;  // Invalid declaration.
```

#### **Important Note:**
If we specify the dimension before the variable name, that feature is applicable only to the first variable in the declaration. If applied to the remaining variables, it results in a compile-time error.

---

Here is the corrected and properly formatted version:  

---

### **Three-Dimensional Array Declarations**  

- `int[] x[]; a;`  
- `int[][][] x;`  
- `int x[][][];`  
- `int[][][] a;`  
- `int[] a[][];`  
- `int[][] a[];`  
- `int[][][] a;`  
- `int[] []a[];`  
- `int[] []x[] a[];`  
- `int[][] a[];`  
- `int[][][] a[][];`  
- `int[] a[][][];`  

---

## **Arrays as Objects in Java**  

- Every array in Java is an object, so we can create arrays using the `new` operator.  
```java
int[] arr = new int[5];  
```  
- For every array type, corresponding classes are available. However, these classes are part of the Java language and are not accessible at the programmer level.  

- To verify the runtime class of an array:  
```java
class Test {
    public static void main(String[] args) {
        int[] x = new int[3];
        System.out.println(x.getClass().getName());  
    }
}
```  
**Output:**  
```
[I
```  
  - `[I` indicates a one-dimensional integer array.  

```java
class Test {
    public static void main(String[] args) {
        int[][] x = new int[3][2];
        System.out.println(x.getClass().getName());
    }
}
```  
**Output:**  
```
[[I
```  
- `[[I` indicates a two-dimensional integer array.  

---


### **Array Size Declaration**  

1. **Specifying Array Size is Mandatory**  
   - At the time of array creation, specifying the size is compulsory. If the size is not specified, a compile-time error occurs.  

   **Valid Code:**  
   ```java
   int[] x = new int[7];  // Array of size 7 created successfully
   ```  

   **Invalid Code:**  
   ```java
   int[] x = new int();  // Error: Array size missing
   ```  

   **Error Message:**  
   ```
   error: array dimension missing
   int[] x = new int();
   ```

2. **Arrays Can Have Size Zero**  
   - Java allows an array with zero elements, meaning an array of size `0` is valid.  

   **Valid Code:**  
   ```java
   int[] x = new int[0];  // Array with zero elements
   ```  
   - Running this code does not cause any errors.  

3. **Negative Array Size Causes a Runtime Exception**  
   - If a negative value is specified as the array size, the program compiles successfully but throws a runtime exception `NegativeArraySizeException`.  

   **Invalid Code:**  
   ```java
   int[] x = new int[-3];  // Runtime Exception
   ```  

   **Error Message at Runtime:**  
   ```
   Exception in thread "main" java.lang.NegativeArraySizeException
   ```

---

### **Valid Data Types for Array Size**  

4. **Allowed Data Types**  
   - The only allowed data types for specifying an array size are:
     - `byte`
     - `short`
     - `char`
     - `int`  
   - Any other type will result in a compile-time error.  

   **Valid Code:**  
   ```java
   byte b = 20;
   short s = 30;
   char c = 40;
   int[] x1 = new int[b];  // Allowed
   int[] x2 = new int[s];  // Allowed
   int[] x3 = new int[c];  // Allowed
   int[] x4 = new int[10]; // Allowed
   ```

5. **Invalid Data Types (Compile-Time Errors)**  
   - Using `long`, `float`, or `double` for array size results in a compile-time error.  

   **Invalid Code:**  
   ```java
   long l = 100;
   int[] x = new int[l];  // Compile-time error
   ```  

   **Error Message:**  
   ```
   error: incompatible types: possible lossy conversion from long to int
   ```

   **Invalid Code:**  
   ```java
   float f = 5.5f;
   int[] x = new int[f];  // Compile-time error
   ```  

   **Error Message:**  
   ```
   error: incompatible types: possible lossy conversion from float to int
   ```

---

### **Maximum Allowed Array Size in Java**  

6. **Maximum Array Size is `Integer.MAX_VALUE` (`2,147,483,647`)**  
   - Java allows creating an array up to the maximum value of an `int`, which is **2,147,483,647**.  

   **Valid Code:**  
   ```java
   int[] x = new int[2147483647];  // Maximum allowed size
   ```

7. **Exceeding Maximum Size Causes a Compile-Time Error**  
   - If the array size exceeds `Integer.MAX_VALUE`, a compile-time error occurs.  

   **Invalid Code:**  
   ```java
   int[] x = new int[2147483648];  // Compile-time error
   ```  

   **Error Message:**  
   ```
   error: integer number too large
   ```

8. **Even Within Limits, Insufficient Memory May Cause a Runtime Error**  
   - If a valid but large array size is used, a runtime exception `OutOfMemoryError` may occur due to insufficient heap memory.  

   **Example Code That May Fail at Runtime:**  
   ```java
   int[] x = new int[1000000000];  // May cause OutOfMemoryError
   ```  

   **Possible Runtime Error Message:**  
   ```
   Exception in thread "main" java.lang.OutOfMemoryError: Java heap space
   ```

---

### **2D Array Creation in Java**  

In Java, two-dimensional arrays are not strictly implemented using a matrix-like structure. Instead, Java follows the **array of arrays** approach to create multidimensional arrays.  

#### **Advantages of Array of Arrays Approach**  
- **Efficient Memory Utilization**: Since rows can have different lengths, memory usage is optimized.  
- **Flexible Structure**: Unlike traditional matrices, Java allows each row to have a different number of columns, which can be useful in various scenarios.  

#### **Example: Creating a 2D Array**  
```java
int[][] x = new int[2][];  // Declaring a 2D array with 2 rows but no fixed columns

x[0] = new int[4];  // First row has 4 columns
x[1] = new int[5];  // Second row has 5 columns
```
---

![alt text](images/image1.png)

### **Jagged Array in Java**  

A **jagged array** is a multidimensional array where each row can have a different number of columns. Java implements multidimensional arrays as arrays of arrays, making jagged arrays possible.  

#### **Example: Creating a Jagged Array**  
```java
public class Test {
    public static void main(String[] args) {
        int[][][] x = new int[2][][];  // 3D array with 2 elements at the first level

        x[0] = new int[3][];  // First element has 3 arrays
        x[0][0] = new int[1]; // First array has 1 element
        x[0][1] = new int[2]; // Second array has 2 elements
        x[0][2] = new int[3]; // Third array has 3 elements

        x[1] = new int[2][2]; // Second element has a 2x2 matrix

        // Assigning values
        x[0][0][0] = 10;
        x[0][1][0] = 20;
        x[0][1][1] = 30;
        x[0][2][0] = 40;
        x[0][2][1] = 50;
        x[0][2][2] = 60;

        x[1][0][0] = 70;
        x[1][0][1] = 80;
        x[1][1][0] = 90;
        x[1][1][1] = 100;
    }
}
```
---


### **Valid and Invalid Array Declarations**  

| **Array Declaration**                 | **Valid / Invalid** | **Reason** |
|---------------------------------------|---------------------|------------|
| `int[] a = new int[];`               | **Invalid**         | Size must be specified. |
| `int[] a = new int[3];`              | **Valid**           | Properly specifies array size. |
| `int[][] a = new int[][];`           | **Invalid**         | Size must be specified for at least the first dimension. |
| `int[][] a = new int[3][];`          | **Valid**           | First dimension is defined, second can be assigned later. |
| `int[][] a = new int[][4];`          | **Invalid**         | First dimension size must be specified. |
| `int[][] a = new int[3][4];`         | **Valid**           | Proper two-dimensional array declaration. |
| `int[][][] a = new int[3][4][5];`    | **Valid**           | Proper three-dimensional array declaration. |
| `int[][][] a = new int[3][4][];`     | **Valid**           | First two dimensions specified, third can be assigned later. |
| `int[][][] a = new int[3][][5];`     | **Invalid**         | Second dimension must be specified before third. |
| `int[][][] a = new int[][4][5];`     | **Invalid**         | First dimension size must be specified. |

In Java, only the **first dimension** of a multidimensional array must be specified at creation time. The other dimensions can be assigned dynamically later.

---


### **1D Array Initialization**  
When you create a 1D array, all elements are automatically set to default values.  

```java
class Test {
    public static void main(String[] args) {
        int[] x = new int[3];  
        System.out.println(x);    // Prints array reference
        System.out.println(x[0]); // Prints default value (0)
    }
}
```

**Output:**
```
[I@6d06d69c   // Memory reference
0             // Default value of int array element
```

---

#### **2D Array Initialization**  
```java
class Test {
    public static void main(String[] args) {
        int[][] x = new int[2][3];  
        System.out.println(x);       // Prints memory reference of 2D array
        System.out.println(x[0]);    // Prints reference of first row
        System.out.println(x[0][0]); // Prints 0 (default value)
    }
}
```

**Output (example memory references):**
```
[[I@5a07e868  // Reference of 2D array
[I@6d06d69c   // Reference of first row (not null)
0             // Default int value
```

- `x` is a **2D array** (`new int[2][3]` means 2 rows, 3 columns).  
- Each row (`x[0]`, `x[1]`) is **automatically created** and filled with `0`.  
- `x[0][0]` accesses an actual integer, which defaults to `0`.  

---

#### **Case That Causes NullPointerException (NPE)**  
```java
class Test {
    public static void main(String[] args) {
        int[][] x = new int[2][];  // Only first dimension initialized
        System.out.println(x[0]);  // Prints null
        System.out.println(x[0][0]);  // Causes NullPointerException
    }
}
```
**Output:**
```
null
Exception in thread "main" java.lang.NullPointerException
```


- `x` is a reference to a **2D array object**.  
- `x[0]` is a reference to the **first row** of the array.  
- `x[0][0]` accesses an **actual element**, which defaults to `0`.


![alt text](images/image2.png)


---
### **Understanding 2D Array Initialization in Java**  

#### **Code Example:**  
```java
class Test {
    public static void main(String[] args) {
        int[][] x = new int[2][3];  
        System.out.println(x);       // Reference of 2D array
        System.out.println(x[0]);    // Reference of first row (not null)
        System.out.println(x[0][0]); // Default value (0)
    }
}
```

#### **Expected Output (Example Addresses):**  
```
[[I@3e2505   // Memory reference of 2D array
[I@5a07e868  // Memory reference of first row (not null)
0            // Default value at x[0][0]
```

#### **Key Points:**
1. **`new int[2][3]` automatically initializes values** → Each row is created and filled with `0` (default for `int`).
2. **`x[0]` is NOT null** → It refers to an array `[0, 0, 0]`.
3. **No NullPointerException (NPE)** → `x[0][0]` exists and holds `0`.

---

### **Case That Causes NullPointerException (NPE)**  
```java
class Test {
    public static void main(String[] args) {
        int[][] x = new int[2][];  // Only first dimension initialized
        System.out.println(x[0]);  // null (since second dimension is not allocated)
        System.out.println(x[0][0]);  // Causes NullPointerException
    }
}
```

#### **Output:**
```
null
Exception in thread "main" java.lang.NullPointerException
```

#### **Why?**
- `x = new int[2][];` initializes only the **first dimension**, but **does not allocate memory for rows**.
- `x[0]` is `null`, so `x[0][0]` throws an **NPE**.

---

- `new int[2][3]` → No NPE, values are `0`
- `new int[2][]` → NPE if accessing `x[0][0]` without allocation


![alt text](images/image3.png)

---

### **Note**

1. **Null Pointer Exception**  
- If we try to perform any operation on `null`, we will get a runtime exception: `NullPointerException`.

2. **Default Initialization of Arrays**  
- When we create an array, each element is initialized with a default value.  
- If we are not satisfied with the default values, we can override them with our customized values.

```java
int[] x = new int[6];  
```
- Default Initialization:  
```
|0|0|0|0|0|0|
```

- After assigning values:
```java
x[0] = 10;
x[1] = 20;
x[2] = 30;
x[3] = 40;
x[4] = 50;
x[5] = 60;
```
- After updation
```
|10|20|30|40|50|60|
```
3. **Invalid Operations on Arrays**
- **Accessing out-of-bounds indices**  
```java
x[6] = 70;  // Invalid - Runtime Exception: ArrayIndexOutOfBoundsException
x[-6] = 50; // Invalid - Runtime Exception: ArrayIndexOutOfBoundsException
```
- **Using non-integer indices**  
```java
x[2.5] = 344; // Invalid - Compile-time Error: Possible loss of precision
```
- **Reason**: Array indices must be of type `int`. A `double` cannot be used as an index.

4. **Out of Range Index Access**
- If we try to access an index outside the valid range (negative or beyond the array size), we get a **runtime exception**:  
`ArrayIndexOutOfBoundsException`.

---
