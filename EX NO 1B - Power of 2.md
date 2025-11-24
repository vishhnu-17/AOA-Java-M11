# EX 1B – Factorial of a Number
## Date : 18/09/2025

## Aim
To write a Java program that reads an integer **N** from the user and calculates the factorial of the given number.

## Algorithm
1. Start  
2. Read an integer **N** from the user.  
3. Initialize a variable **i = 1**.  
4. Loop from **j = 1** to **N**:  
   - Multiply **i** by **j** and store the result in **i**.  
5. After the loop ends, print the value of **i** (which is **N!**).  
6. Stop  

### Developed By: **Kurapati Vishnu Vardhan Reddy**  
### Register Number: **212223040103**



## Program
```java
import java.util.*;
public class Main{
    public static void main(String[] args){
        Scanner input = new Scanner(System.in);
        int n = input.nextInt();
        int i = 1;
        for(int j = 1; j <= n; j++){
            i = i * j;
        }
        System.out.println(i);
    }
}
```
### Output:
<img width="387" height="198" alt="image" src="https://github.com/user-attachments/assets/b0ff48f2-693e-468f-a76d-d4db1d6bb21d" />

### Result:
The program successfully calculates and displays the factorial of a given number N.

