# Permutations

## Intuition

- loop through each element in array
- swap that element in ind with everything from ind to n using i variable

## Example 

Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

```py
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        n=len(nums)
        ans=[]
        ind=0
        self.solve(nums, ind, n, ans)
        return ans
    
    def solve(self, nums,ind,n,ans):
        if ind==n:
            ans.append(nums.copy())
            return

        for i in range(ind,n):
            # swapping from current index ind to n
            self.swap(nums,ind,i)
            # ind+1 because we are moving to the next index to start swapping from ind to n
            self.solve(nums, ind+1, n, ans)
            # backtrack
            self.swap(nums,ind,i)
    def swap(self, nums, ind,i):
        temp=nums[ind]
        nums[ind]=nums[i]
        nums[i]=temp

```