### Prefix sum

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


