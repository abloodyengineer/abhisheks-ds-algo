# Insertion Sort

## Intuition - Opposite of Bubble sort
- Move minimum to front by adjacent swaps
- Loop i from beginning to end of list
- Loop j from i to 0
- swap j with j-1 if nums[j]< nums[j-1], that is, moving the min to beginning
- after i goes from 0 to n, the array will be sorted

## Code
```py
class Solution:
    # Insertion sort- bring lower value to beginning - compare each element with its left element, swap if element is smaller - O(n^2) - TLE
    # Best case O(n)
    def sortArray(self, nums: List[int]) -> List[int]:
        n=len(nums)
        for i in range(n):
            for j in range(i,0,-1):
                if nums[j]<nums[j-1]:
                    self.swap(j-1,j,nums)
        return nums
    def swap(self, first, second, nums):
        temp=nums[first]
        nums[first]=nums[second]
        nums[second]=temp
```

## Time complexity 

**O(N^2)**

## Space Complexity

**O(1)**

## Study Further

- [Geek For Geeks](https://www.geeksforgeeks.org/insertion-sort/){:target="_blank"}