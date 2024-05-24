# Bubble Sort

## Intuition
- Move maximun to end by adjacent swaps
- Loop i from end of list to beginning
- Loop j from 0 to i(dont include i)
- swap j with j+1 if j>j+1, that is, moving the max to end
- after i goes from n-1 to 0, the array will be sorted

## Code
```py
# Bubble sort- move max to end - O(n^2) - TLE
def sortArray(self, nums: List[int]) -> List[int]:
    n=len(nums)
    for i in range(n-1,-1,-1):
        for j in range(0, i):
            if nums[j]>nums[j+1]:
                self.swap(j,j+1,nums)
    return nums
def swap(self, first, second, nums):
    temp=nums[first]
    nums[first]=nums[second]
    nums[second]=temp
```

```py
class Solution:
    # Bubble sort- move max to end - little optimized - O(n^2), best case O(n) if array already sorted - TLE
    def sortArray(self, nums: List[int]) -> List[int]:
        n=len(nums)
        for i in range(n-1,-1,-1):
            swapped=0
            for j in range(0, i):
                if nums[j]>nums[j+1]:
                    self.swap(j,j+1,nums)
                    swapped=1
            if swapped==0:
                return nums
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

- [Geek For Geeks](https://www.geeksforgeeks.org/bubble-sort/){:target="_blank"}