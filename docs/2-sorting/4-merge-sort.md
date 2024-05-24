# Merge Sort

## Intuition

- Calculate mid = (high+low)/2
- Call merge sort recursively from low to mid
- Call merge sort recursively from mid+1 to high
- Finally merge the two halves from low to high using mid

## Code
```py
class Solution:
    # Merge-sort - O(nlogn)
    def sortArray(self, nums: List[int]) -> List[int]:
        n=len(nums)
        self.mergeSort(nums,0, n-1)
        return nums

    def mergeSort(self, nums, low, high):
        if low>=high:
            return
        mid=(high+low)//2
        self.mergeSort(nums, low, mid)
        self.mergeSort(nums, mid+1, high)
        self.merge(nums, low,mid,high)

    def merge(self, nums, low,mid,high):
        temp=[]
        left=low
        right=mid+1
        while left<=mid and right<=high:
            if nums[left]<nums[right]:
                temp.append(nums[left])
                left+=1
            else:
                temp.append(nums[right])
                right+=1
        while left<=mid:
            temp.append(nums[left])
            left+=1
        while right<=high:
            temp.append(nums[right])
            right+=1
        for i in range(low,high+1):
            nums[i]=temp[i-low]
```

## Time complexity 

**O(nlogn)**

## Space Complexity

**O(n) + recursion stack**
Additional space is required for the temporary array used during merging.

## Study Further

- [Geek For Geeks](https://www.geeksforgeeks.org/merge-sort/){:target="_blank"}