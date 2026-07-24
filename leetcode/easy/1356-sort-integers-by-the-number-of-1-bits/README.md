# Sort Integers by The Number of 1 Bits

![Difficulty](https://img.shields.io/badge/Difficulty-Easy-green)

## Problem

You are given an integer array `arr`. Sort the integers in the array in ascending order by the number of `1`'s in their binary representation and in case of two or more integers have the same number of `1`'s you have to sort them in ascending order.

Return  *the array after sorting it*.

 

 **Example 1:** 

```
Input: arr = [0,1,2,3,4,5,6,7,8]
Output: [0,1,2,4,8,3,5,6,7]
Explantion: [0] is the only integer with 0 bits.
[1,2,4,8] all have 1 bit.
[3,5,6] have 2 bits.
[7] has 3 bits.
The sorted array by bits is [0,1,2,4,8,3,5,6,7]

```

 **Example 2:** 

```
Input: arr = [1024,512,256,128,64,32,16,8,4,2,1]
Output: [1,2,4,8,16,32,64,128,256,512,1024]
Explantion: All integers have 1 bit in the binary representation, you should just sort them in ascending order.

```

 

 **Constraints:** 

- 1 <= arr.length <= 500
- 0 <= arr[i] <= 104

## Solution

**Language:** Java  
**Runtime:** 8 ms (beats 67.10%)  
**Memory:** 46.6 MB (beats 63.24%)  
**Submitted:** 2026-07-24T18:19:57.200Z  

```java
class Solution {
    public int[] sortByBits(int[] arr) {

        //Nabamita
        Integer[] nums = new Integer[arr.length];

        
        for (int i = 0; i < arr.length; i++) {
            nums[i] = arr[i];
        }

        Arrays.sort(nums, (a, b) -> {
            int bitsA = Integer.bitCount(a);
            int bitsB = Integer.bitCount(b);

            
            if (bitsA != bitsB) {
                return bitsA - bitsB;
            }

          
            return a - b;
        });

      
        for (int i = 0; i < arr.length; i++) {
            arr[i] = nums[i];
        }

        return arr;
    }
} 
    

```

---

[View on LeetCode](https://leetcode.com/problems/sort-integers-by-the-number-of-1-bits/)