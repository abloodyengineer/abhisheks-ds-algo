# Subsets - 2 - Array nums that may contain duplicates, ans cannot have duplicates

## Intuition

- As there might be duplicates, sort the array to group duplicates
- we will start off with an empty array and put that in ans array
- we will loop through each element, and put it in ans array if not duplicate
- if duplicate, continue

## Example

Input: nums = [1,2,2]
Output: [[],[1],[1,2],[1,2,2],[2],[2,2]]

```py
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]: 
        nums.sort()
        n=len(nums)
        ans=[]
        ind=0
        self.solve(nums, [], ind, n, ans )
        return ans
    
    def solve(self, nums, arr, ind, n, ans):
        print(ind,arr)
        ans.append(arr.copy())
        for i in range(ind,n):
            if i!=ind and nums[i]==nums[i-1]:
                continue
            arr.append(nums[i])
            # here it is i+1 and not ind+1 as we are moving to the next i. This is ind in permutation 1
            self.solve(nums, arr, i+1, n, ans)
            arr.pop()
```