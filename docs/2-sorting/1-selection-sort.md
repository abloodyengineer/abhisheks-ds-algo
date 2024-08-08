# Selection Sort

## Intuition
- Move minimum to front
- Loop through the list n times
- In each loop, take the i-th element as temp mini
- find the minimum in the array from i to n
- swap mini with i-th element
- continue by increasing i in each step

## Code
```py
class Solution:
    # Selection sort- move min to front - O(n^2) - TLE
    def sortArray(self, nums: List[int]) -> List[int]:
        n=len(nums)
        for i in range(n-1):
            mini=i
            for j in range(i,n):
                if nums[j]<nums[mini]:
                    mini=j
            self.swap(i,mini, nums)
        return nums

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

- [Geek For Geeks](https://www.geeksforgeeks.org/selection-sort/){:target="_blank"}