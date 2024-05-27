# Remove duplicates from sorted array

[Problem link - Leetcode](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/){:target="_blank"}


## Intuition - Brute force - using set

> Time complexity - O(nlogn)

> Space complexity - O(n) for set

- store nums in a set and sort it. make sure tor assign this to nums
- return the length of nums, which is now a set

```py
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        nums[:]=sorted(set(nums))
        return len(nums)
```

## Intuition - Optimal force - using two pointers

> Time complexity - O(n)

> Space complexity - O(1)

- take left = 0, right = 0
- loop right from 0 to n
- if nums[right] is not equal to nums[left], assign nums[right] nums[left+1] and increment left by 1. This means, when we fin a new element, we place it next to first occurence of old element
- length of unique elements will be left+1

```py
class Solution:
	# Optimal approach - 2 pointers - time - O(n) - space - O(1)
    def removeDuplicates(self, nums: List[int]) -> int:
        n=len(nums)
        left=0
        right=0
        while right < n:
            if nums[right] != nums[left]:
                nums[left+1]=nums[right]
                left+=1
            right+=1
        return left+1

```
