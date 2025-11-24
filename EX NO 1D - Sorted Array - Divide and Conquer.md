
# EX 1D Sorted Array using Divide and Conquer Approach.
## DATE: 18-09-2025
## AIM:
To write a Java program to for given constraints.
Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.

The overall run time complexity should be O(log (m+n)).

## Algorithm
1. Merge both sorted arrays into one sorted array using two pointers.  
2. Append remaining elements from either array once one pointer reaches the end.  
3. Compute the middle index of the merged array.  
4. If the merged length is even, return the average of the two middle elements.  
5. If odd, return the single middle element as the median.
  

### Developed By: Kurapati Vishnu Vardhan Reddy
### Register Number: 212223040103

## Program:
```java
import java.util.*;

public class MedianOfArrays {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int m = sc.nextInt();
        int[] nums1 = new int[m];
        for (int i = 0; i < m; i++) nums1[i] = sc.nextInt();
        int n = sc.nextInt();
        int[] nums2 = new int[n];
        for (int i = 0; i < n; i++) nums2[i] = sc.nextInt();
        System.out.println("Median of the two sorted arrays = " + findMedianSortedArrays(nums1, nums2));
    }

    public static double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int[] merged = new int[nums1.length + nums2.length];
        int i = 0, j = 0, k = 0;
        while (i < nums1.length && j < nums2.length) {
            if (nums1[i] < nums2[j]) merged[k++] = nums1[i++];
            else merged[k++] = nums2[j++];
        }
        while (i < nums1.length) merged[k++] = nums1[i++];
        while (j < nums2.length) merged[k++] = nums2[j++];
        int mid = merged.length / 2;
        if (merged.length % 2 == 0) return (merged[mid - 1] + merged[mid]) / 2.0;
        return merged[mid];
    }
}

```

## Output:

<img width="889" height="353" alt="image" src="https://github.com/user-attachments/assets/d058d85f-6cd3-4e1f-ba5c-c6b2e445fedd" />

## Result:
The program successfully implemented and the expected output is verified.
