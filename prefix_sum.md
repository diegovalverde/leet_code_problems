### Prefix sum
https://leetcode.com/problems/continuous-subarray-sum

Given a list of non-negative numbers and a target integer k, write a function to check if the array has a continuous subarray of size at least 2 that sums up to a multiple of k, that is, sums up to n*k where n is also an integer.

 

Example 1:

Input: [23, 2, 4, 6, 7],  k=6
Output: True
Explanation: Because [2, 4] is a continuous subarray of size 2 and sums up to 6.
Example 2:

Input: [23, 2, 6, 4, 7],  k=6
Output: True
Explanation: Because [23, 2, 6, 4, 7] is an continuous subarray of size 5 and sums up to 42.
 

Constraints:

The length of the array won't exceed 10,000.
You may assume the sum of all the numbers is in the range of a signed 32-bit integer.
the **prefix sum**, **cumulative sum**, **inclusive scan**, or simply **scan** of a sequence of numbers *x*0, *x*1, *x*2, ... is a second sequence of numbers *y*0, *y*1, *y*2.

$y_0 = x_0$

$y_1 = x_0 + x_1$

$y_2 = x_0 + x_1 + X_2$

and so on.

If you calculate the prefix sum, then you can see that $sum(x_i,...,x_j) = y_j - y_i$.

Now, suppose that in your sequence $sum(x_i,...x_j) \% k = 0$.
$\implies (y_j - y_i) \%k = 0$

$\implies y_j \%k - y_i \%k = 0$

So that $sum(x_i,...x_j) \% k = 0\iff y_j \% k = y_i \% k$

for this reason:

```python

def checkSubarraySum(nums, k):
    y = 0 # the prefix sum
    m = {}
    for i, x in enumerate(nums):
      y += x				
      if y % k in m and i - m[y % k] >= 2: 
        return True  
      m[y % k] = i
    return False
```


