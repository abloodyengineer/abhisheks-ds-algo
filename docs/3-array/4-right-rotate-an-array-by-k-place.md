# Left rotate an array by k places

[Problem link - Leetcode](https://leetcode.com/problems/rotate-array/description/){:target="_blank"}


## Intuition 1 - using temp array

> Time complexity - O(n+d)

> Space complexity - O(N)

- store last k elements in a temp array
- loop through array from end to k
- move elements from 0 to n-k to end
- fill up starting k places with elements from temp

```py
class Solution:
    # Time -O(n+d) Extra Space - O(N)
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        n=len(nums)
        new_k=k%n
        temp=nums[n-new_k:n]
        for i in range(n-1,new_k-1,-1):
            nums[i]=nums[i-new_k]
        for i in range(len(temp)):
            nums[i]=temp[i]
```

## Intuition 2 - using reversing technique

> Time complexity - O(n)

> Space complexity - O(1)

- Reverse 0 to n-k
- Reverse n-k to end
- Reverse 0 to end

```py
class Solution:
    # time - O(N) extra space - O(1) 
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        n=len(nums)
        new_k=k%n
        self.reverse(0, n-new_k, nums)
        self.reverse(n-new_k, n, nums)
        self.reverse(0,n,nums)
    def reverse(self, left, right,nums):
        while left<right-1:
            temp=nums[left]
            nums[left]=nums[right-1]
            nums[right-1]=temp
            left+=1
            right-=1
```