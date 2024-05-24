# Quick Sort

> Not suitable if array is sorted

## Intuition

- Call pivot which appoints a pivot, moves everything smaller than pivot to left and larger to right of pivot. move the pivot to the correct place. Return the pivot index
- Call quick sort recursively again from low to pivot_index-1
- Call quick sort recursively again from pivot_index+1 to high
- Pivot function:
    - take the low index as pivot
    - i=low, j=high
    - while i <= high, and nums[i] <= pivot, increment i
    - while j>=low , and nums[j] > pivot, decrement j
    - What this means is we stop i when i is at an index whose value is higher than pivot and j at an index whose value is smaller than equal to pivot.
    - if i and j did not cross, we can swap i and j so that smaller is at left, larger is at right
    - if i and j cross each other, means we have done all movement, now we can place the pivot in its correct index.
    - correct index of pivot will be j as it stands at one place left of the index which is just higher than pivot
    - so, swap low(pivot index) with j
    - also return j as the pivot index, so that next recursion calls can be from 0 to j-1 and j+1 to end, that is excluding j
 
## Code
```py
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        n=len(nums)
        self.quick_sort(nums,0,n-1)
    
    def quick_sort(self, nums, low,high):
        if low<high:

            pivot_index=self.pivot(nums,low,high)
            self.quick_sort(nums,low,pivot_index-1)
            self.quick_sort(nums,pivot_index+1, high)
    
    def pivot(self, nums, low, high):
        pivot =nums[low]
        i=low
        j=high
        while i<j:
            while i<=high and nums[i]<=pivot: #less than equal to to consider the equal to scenario
                i+=1
            while j>=low and nums[j]>pivot: #just greater than as equal to scenario checked above already
                j-=1
            if i<j:
                self.swap(i,j,nums)
        self.swap(low,j, nums)
        return j

                
    def swap(self, first, second, nums):
        temp=nums[first]
        nums[first]=nums[second]
        nums[second]=temp
```

## Time complexity 

**O(nlogn)**

## Space Complexity

**O(1)**

## Study Further

- [Geek For Geeks](https://www.geeksforgeeks.org/quick-sort/){:target="_blank"}