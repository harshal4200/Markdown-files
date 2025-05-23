



# Selection Sort Algorithm #

**Problem Statement**
- Given an array of **N integers**, write a program to implement
the selection sorting algorithm.
---
### Examples: ###

**Example 1:**
- **Input:** `N=6, array[] = {13,46,24,52,20,9}`
- **Output:** `9,13,20,24,46,52`
- **Explanation:** After sorting the array is: `9,13,20,24,46,52`
---
## Solution

>Disclaimer:
 _Don't jump directly to the solution, try it out yourself first._

**Approach:**

- The algorithm steps are as follows:

1. First, we will select the range of the unsorted array using a loop (say i) that indicates the starting index of the range.
   The loop will run forward from 0 to n-1. The value i = 0 means the range is from 0 to n-1, and similarly, i = 1 means the range is from 1 to n-1, and so on.

2. Now, in each iteration, we will select the minimum element from the range of the unsorted array using an inner loop.

3. After that, we will swap the minimum element with the first element of the selected range(in step 1).

4. Finally, after each iteration, we will find that the array is sorted up to the first index of the range.

---

**Note:**
- Here, after each iteration, the array becomes sorted up to the first index of the range. That is why the starting index of the range increases by 1 after each iteration. This increment is achieved by the outer loop and the starting index is represented by variable i in the following code. And the inner loop(i.e. j) helps to find the minimum element of the range [i…..n-1].

---

**Dry run:**
- The following dry run will clarify the concepts:

- Assume the given array is: `{7, 5, 9, 2, 8}`

**Outer loop iteration 1:**
- The range will be the whole array starting from the 1st index as this is the first iteration. The minimum element of this range is 2(found using the inner loop).
  
![image](https://static.takeuforward.org/wp/uploads/2023/03/Screenshot-2023-03-13-223901.png)

- `2` is minimum

**Outer loop iteration 2:**
- The range will be from the [2nd index to the last index] as the array is sorted up to the first index. The minimum element of this range is 5(found using the inner loop).
  
![image](https://static.takeuforward.org/wp/uploads/2023/03/Screenshot-2023-03-13-224021.png)

- After iteration `2`, the elements up to the 2nd index are sorted.

**Outer loop iteration 3:**
- The range will be from the [3rd index to the last index]. The minimum element of this range is 7(found using the inner loop).
  
![image](https://static.takeuforward.org/wp/uploads/2023/03/Screenshot-2023-03-13-225729.png)


**Outer loop iteration 4:**
- The range will be from the [4th index to the last index]. The minimum element of this range is 8(found using the inner loop).
  
![image](https://static.takeuforward.org/wp/uploads/2023/03/Screenshot-2023-03-13-225822.png)

---

- So, after 4 iterations(i.e. n-1 iterations where n = size of the array), the given array is sorted.

``` java
import java.util.*;

public class SelectSort {
    static void selection_sort(int arr[], int n) {
        for (int i = 0; i < n - 1; i++) {
            int mini = i;
            for (int j = i + 1; j < n; j++) {
                if (arr[j] < arr[mini]) {
                    mini = j;
                }
            }
            //swap
            int temp = arr[mini];
            arr[mini] = arr[i];
            arr[i] = temp;
        }

        System.out.println("After selection sort:");
        for (int i = 0; i < n; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();
    }

    public static void main(String args[]) {

        int arr[] = {13, 46, 24, 52, 20, 9};
        int n = arr.length;
        System.out.println("Before selection sort:");
        for (int i = 0; i < n; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();
        selection_sort(arr, n);
    }
}
```


---

**Output:**
```
 Before selection sort:
 13 46 24 52 20 9
 After selection sort:
 9 13 20 24 46 52
```
**Time Complexity:**
- `O(N^2)`, (where N = size of the array), for the best, worst, and average cases.

- Reason: If we carefully observe, we can notice that the outer loop, say i, is running from 0 to n-2 i.e. n-1 times, and for each i, the inner loop j runs from i to n-1. For, i = 0, the inner loop runs n-1 times, for i = 1, the inner loop runs n-2 times, and so on. So, the total steps will be approximately the following: (n-1) + (n-2) + (n-3) + ……..+ 3 + 2 + 1. The summation is approximately the sum of the first n natural numbers i.e. (n*(n+1))/2. The precise time complexity will be O(n2/2 + n/2). Previously, we have learned that we can ignore the lower values as well as the constant coefficients. So, the time complexity is O(n2). Here the value of n is N i.e. the size of the array.

**Space Complexity: `O(1)`**





