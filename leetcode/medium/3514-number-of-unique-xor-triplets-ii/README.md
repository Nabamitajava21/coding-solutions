# Number of Unique XOR Triplets II

![Difficulty](https://img.shields.io/badge/Difficulty-Medium-yellow)

## Problem

You are given an integer array `nums`.

A  **XOR triplet**  is defined as the XOR of three elements `nums[i] XOR nums[j] XOR nums[k]` where `i <= j <= k`.

Return the number of  **unique**  XOR triplet values from all possible triplets `(i, j, k)`.

 

 **Example 1:** 

 **Input:**  nums = [1,3]

 **Output:**  2

 **Explanation:** 

The possible XOR triplet values are:

- (0, 0, 0) → 1 XOR 1 XOR 1 = 1
- (0, 0, 1) → 1 XOR 1 XOR 3 = 3
- (0, 1, 1) → 1 XOR 3 XOR 3 = 1
- (1, 1, 1) → 3 XOR 3 XOR 3 = 3

The unique XOR values are `{1, 3}`. Thus, the output is 2.

 **Example 2:** 

 **Input:**  nums = [6,7,8,9]

 **Output:**  4

 **Explanation:** 

The possible XOR triplet values are `{6, 7, 8, 9}`. Thus, the output is 4.

 

 **Constraints:** 

- 1 <= nums.length <= 1500
- 1 <= nums[i] <= 1500

## Solution

**Language:** Java  
**Runtime:** 198 ms (beats 89.09%)  
**Memory:** 46.9 MB (beats 63.64%)  
**Submitted:** 2026-07-24T18:17:46.304Z  

```java
class Solution {
    public int uniqueXorTriplets(int[] nums) {
        //Nabamita
        boolean[] present = new boolean[2048];

        
        for (int num : nums) {
            present[num] = true;
        }

        
        int[] values = new int[2048];
        int m = 0;
        for (int i = 0; i < 2048; i++) {
            if (present[i]) {
                values[m++] = i;
            }
        }

        
        boolean[] pairXor = new boolean[2048];

        for (int i = 0; i < m; i++) {
            for (int j = i; j < m; j++) {
                pairXor[values[i] ^ values[j]] = true;
            }
        }

       
        boolean[] tripletXor = new boolean[2048];

        for (int i = 0; i < 2048; i++) {
            if (pairXor[i]) {
                for (int j = 0; j < m; j++) {
                    tripletXor[i ^ values[j]] = true;
                }
            }
        }

       
        int ans = 0;
        for (boolean x : tripletXor) {
            if (x) ans++;
        }

        return ans;
    }
}
    

```

---

[View on LeetCode](https://leetcode.com/problems/number-of-unique-xor-triplets-ii/)