
# EX 1C Valid Pairs using Brute Force Approach
## DATE: 18-09-2025
## AIM:
To write a Java program to for given constraints.
Given an integer array nums and an integer k, return the number of pairs (i, j) where i < j such that |nums[i] - nums[j]| == k.

The value of |x| is defined as:

x if x >= 0.
-x if x < 0.

## Algorithm
1. Use a frequency map to count how many previously seen numbers differ from the current by k.  
2. For each number, add counts of (num - k) and (num + k) from the map to the answer.  
3. Update the frequency of each number as you traverse the array.  
4. Perform a single pass through the array while maintaining frequency counts.  
5. Return the accumulated count of valid difference-k pairs.

### Developed By: Kurapati Vishnu Vardhan Reddy
### Register Number: 212223040103

## Program:
```java
import java.util.*;
public class CountPairsWithDifference {
    public static int countKDifference(int[] nums, int k) {
        Map<Integer,Integer> freq=new HashMap<>();
        int count=0;
        
        for(int num:nums){
            count+=freq.getOrDefault(num-k,0);
            count+=freq.getOrDefault(num+k,0);
            freq.put(num,freq.getOrDefault(num, 0) + 1);
        }
        return count;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }
        int k = sc.nextInt();
        int result = countKDifference(nums, k);
        System.out.println(result);
        sc.close();
    }
}
```

## Output:
<img width="420" height="297" alt="image" src="https://github.com/user-attachments/assets/1866a1a5-b49f-4d8c-91cf-fd67dc665b7d" />

## Result:
The program successfully implemented and the expected output is verified.
