# Data Structures and Algorithms

## 1. 1929. Concatenation of Array

### Problem Statement

Given an integer array `nums` of length `n`, you want to create an array `ans` of length `2n` where `ans[i] == nums[i]` and `ans[i + n] == nums[i]` for `0 <= i < n` (0-indexed).

Specifically, `ans` is the concatenation of two `nums` arrays.

Return the array `ans`.

### Example 1

```
Input: nums = [1,2,1]
Output: [1,2,1,1,2,1]
Explanation: The array ans is formed as follows:
- ans = [nums[0], nums[1], nums[2], nums[0], nums[1], nums[2]]
- ans = [1,2,1,1,2,1]
```

### Example 2

```
Input: nums = [1,3,2,1]
Output: [1,3,2,1,1,3,2,1]
Explanation: The array ans is formed as follows:
- ans = [nums[0], nums[1], nums[2], nums[3], nums[0], nums[1], nums[2], nums[3]]
- ans = [1,3,2,1,1,3,2,1]
```

### Solution

```java
class Solution {
    public int[] getConcatenation(int[] nums) {
        int n = nums.length;
        int[] ans = new int[2 * n];
        for (int i = 0; i < n; i++) {
            ans[i] = nums[i];
            ans[i + n] = nums[i];
        }
        return ans;
    }
}
```

---

## 2. Pattern Recognition

This question uses the **Array Copy Pattern**.

This pattern will be useful for the following problems:

- Merge Two Arrays
- Merge Sorted Arrays
- Rotate Array
- Duplicate Zeros
- Move Zeroes
- Reshape Matrix

---

## 3. 977. Squares of a Sorted Array

### Problem Statement

Given:

A sorted integer array (can contain negative numbers).

Task:

Return a new array containing the square of every number, also sorted in non-decreasing order.

Input:

```
[-4,-1,0,3,10]
```

Square:

```
[16,1,0,9,100]
```

Output:

```
[0,1,9,16,100]
```

### Approach

**Two Pointers**

#### Observation

Negative numbers become positive after squaring.

Example:

- (-7)² = 49
- 11² = 121

The largest square will always be at either end of the array.

That's why we compare:

- Left element's square
- Right element's square

#### Step-by-step

Array: `[-4,-1,0,3,10]`

```
left = 0
right = 4
index = 4

16 vs 100
100 is bigger
result = [_,_,_,_,100]
right--
index--

16 vs 9
16 is bigger
result = [_,_,_,16,100]
left++
index--

1 vs 9
9 is bigger
result = [_,_,9,16,100]
right--
index--
```

#### Algorithm

1. Create result array.
2. `left = 0`
3. `right = n-1`
4. `index = n-1`
5. While `left <= right`:
   - `leftSquare = arr[left] * arr[left]`
   - `rightSquare = arr[right] * arr[right]`
   - If `leftSquare >= rightSquare`:
     - `result[index] = leftSquare`
     - `left++`
   - Else:
     - `result[index] = rightSquare`
     - `right--`
   - `index--`
6. Return result

### Complexity Analysis

- **Time Complexity:** O(n)
- **Space Complexity:** O(n)

### Solution

```java
import java.util.Arrays;

class Main {
    public static void main(String[] args) {
        int[] arr = {-4, -1, 0, 3, 10};
        int n = arr.length;
        int[] result = new int[n];
        int left = 0;
        int right = arr.length - 1;
        int index = arr.length - 1;
        while (left <= right) {
            if (arr[left] * arr[left] >= arr[right] * arr[right]) {
                result[index] = arr[left] * arr[left];
                left++;
                index--;
            } else {
                result[index] = arr[right] * arr[right];
                right--;
                index--;
            }
        }
        System.out.println(Arrays.toString(result));
    }
}
```
