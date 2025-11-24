
# EX 1E Integer Multiplication using Divide and Conquer Approach(Strassen’s algorithm).
## DATE: 18-09-2025
## AIM:
To write a Java program to for given constraints.
You are given two square matrices A and B of size n × n (where n is a power of 2). Your task is to compute their matrix product using Strassen’s Matrix Multiplication algorithm and return the resulting matrix.

Unlike traditional matrix multiplication which takes O(n3)O(n^3)O(n3) time, Strassen’s algorithm improves this by reducing the number of recursive multiplications from 8 to 7, achieving approximately O(n2.81)O(n^{2.81})O(n2.81) complexity.
## Algorithm
1. Recursively split both matrices into four quadrants until size 1×1 is reached.  
2. Use Strassen’s seven formula-based matrix products instead of eight normal multiplications.  
3. Form the intermediate matrices M1–M7 using combinations of additions and subtractions.  
4. Combine the resulting four C-quadrants (C11, C12, C21, C22) using Strassen’s recombination formulas.  
5. Merge these four quadrants back into a single result matrix and return it.

### Developed By: Kurapati Vishnu Vardhan Reddy
### Register Number: 212223040103

## Program:
```java
import java.util.Scanner;

public class StrassenMatrix {

    // Add two matrices
    static int[][] add(int[][] A, int[][] B) {
        int n = A.length;
        int[][] C = new int[n][n];
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                C[i][j] = A[i][j] + B[i][j];
        return C;
    }

    // Subtract matrix B from A
    static int[][] subtract(int[][] A, int[][] B) {
        int n = A.length;
        int[][] C = new int[n][n];
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                C[i][j] = A[i][j] - B[i][j];
        return C;
    }

    // Strassen recursive multiplication
    static int[][] strassen(int[][] A, int[][] B) {
    int n = A.length;
    int[][] result = new int[n][n];

    // Base case
    if (n == 1) {
        result[0][0] = A[0][0] * B[0][0];
        return result;
    }

    int newSize = n / 2;
    int[][] A11 = new int[newSize][newSize];
    int[][] A12 = new int[newSize][newSize];
    int[][] A21 = new int[newSize][newSize];
    int[][] A22 = new int[newSize][newSize];

    int[][] B11 = new int[newSize][newSize];
    int[][] B12 = new int[newSize][newSize];
    int[][] B21 = new int[newSize][newSize];
    int[][] B22 = new int[newSize][newSize];

    // Divide matrices into 4 submatrices
    for (int i = 0; i < newSize; i++) {
        for (int j = 0; j < newSize; j++) {
            A11[i][j] = A[i][j];
            A12[i][j] = A[i][j + newSize];
            A21[i][j] = A[i + newSize][j];
            A22[i][j] = A[i + newSize][j + newSize];

            B11[i][j] = B[i][j];
            B12[i][j] = B[i][j + newSize];
            B21[i][j] = B[i + newSize][j];
            B22[i][j] = B[i + newSize][j + newSize];
        }
    }

    // Compute 7 products (Strassen's formulas)
    int[][] M1 = strassen(add(A11, A22), add(B11, B22));
    int[][] M2 = strassen(add(A21, A22), B11);
    int[][] M3 = strassen(A11, subtract(B12, B22));
    int[][] M4 = strassen(A22, subtract(B21, B11));
    int[][] M5 = strassen(add(A11, A12), B22);
    int[][] M6 = strassen(subtract(A21, A11), add(B11, B12));
    int[][] M7 = strassen(subtract(A12, A22), add(B21, B22));

    // Combine intermediate products into final quadrants
    int[][] C11 = add(subtract(add(M1, M4), M5), M7);
    int[][] C12 = add(M3, M5);
    int[][] C21 = add(M2, M4);
    int[][] C22 = add(subtract(add(M1, M3), M2), M6);

    // Combine quadrants into result matrix
    for (int i = 0; i < newSize; i++) {
        for (int j = 0; j < newSize; j++) {
            result[i][j] = C11[i][j];
            result[i][j + newSize] = C12[i][j];
            result[i + newSize][j] = C21[i][j];
            result[i + newSize][j + newSize] = C22[i][j];
        }
    }

    return result;
}

    // Function to print matrix
    static void printMatrix(int[][] matrix) {
        for (int[] row : matrix) {
            for (int val : row)
                System.out.print(val + " ");
            System.out.println();
        }
    }

    // Main method to get input and run Strassen multiplication
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Read size of matrix
        //System.out.print("Enter matrix size (power of 2): ");
        int n = sc.nextInt();

        int[][] A = new int[n][n];
        int[][] B = new int[n][n];

        // Input Matrix A
        //System.out.println("Enter elements of matrix A:");
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                A[i][j] = sc.nextInt();

        // Input Matrix B
        //System.out.println("Enter elements of matrix B:");
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                B[i][j] = sc.nextInt();

        // Multiply using Strassen
        int[][] result = strassen(A, B);

        // Output the result matrix
        System.out.println("Result of Strassen Matrix Multiplication:");
        printMatrix(result);
    }
}

```

## Output:

<img width="973" height="333" alt="image" src="https://github.com/user-attachments/assets/b644c837-15d5-48a9-9f64-e080ce7cee50" />


## Result:
The program successfully implemented and the expected output is verified.
