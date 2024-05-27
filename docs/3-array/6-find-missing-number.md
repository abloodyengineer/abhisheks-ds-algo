# Move zeroes to end

[Problem link - Leetcode](https://leetcode.com/problems/move-zeroes/description/){:target="_blank"}


## Intuition 1 - Good solution

> Time complexity - O(2n)

> Space complexity - O(n)

- initialize a temp array with all 0s
- loop through the nums array, and mark the indexes corresponding to the elements with 1, i.e, if 2 is present in nums, mark arr[2]=1 and so on
- loop through temp array. whichever index is marked 0 is the missing number

```py
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        n=len(nums)
        arr=[0]*(n+1)
        for i in range(n):
            arr[nums[i]]=1
        for i in range(n+1):
            if arr[i]==0:
                return i
```

## Intuition 2 - Optimal solution 1 - sum

> Time complexity - O(n)

> Space complexity - O(1)

- Find sum on first n natural numbers
- find sum of given nums array
- the difference is the missing number

```py
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        n=len(nums)
        nsum=sum(range(n+1))
        actual_sum=sum(nums)
        return nsum-actual_sum
```

## Intuition 3 - Optimal solution 2 - xor

This can be solved using xor as well. Hint - Xor with first n natural numbers. the answer is the missing number because **a^a=0**

so every number cancels out except the missing number