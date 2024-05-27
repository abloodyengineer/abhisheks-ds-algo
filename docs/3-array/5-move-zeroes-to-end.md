# Move zeroes to end

[Problem link - Leetcode](https://leetcode.com/problems/move-zeroes/description/){:target="_blank"}


## Intuition 1 - optimal

> Time complexity - O(n)

> Space complexity - O(1)

- initialize a variable zero_index with 0
- loop through array from 0 to end
- if element is non zero, swap it with the last zero_index
- increment zero_index as zero moved to the right by one place due to swap
- slowly all non zeros will move to left and all zeros to end

```py
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        n=len(nums)
        zero_index=0
        for i in range(n):
            if nums[i]!=0:
                self.swap(i,zero_index, nums)
                zero_index+=1
        
    def swap(self, first, second, nums):
        temp=nums[first]
        nums[first]=nums[second]
        nums[second]=temp
```