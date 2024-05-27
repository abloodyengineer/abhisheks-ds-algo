# Longest Sub-Array with Sum K

[Problem link - GFG](https://www.geeksforgeeks.org/problems/longest-sub-array-with-sum-k0809/1){:target="_blank"}


# Only positives

## Intuition - Better approach using hashmap

> Time complexity - O(nlogn) n for loop, logn to find in hashmap

> Space complexity - O(n) for hashmap

- create a hashmap, we will store cumulative sum until i as key, and i as value, in hashmap
- Loop through array using i
- keep a cumulative sum of elements up to i
- if sum == k, then max_len should be equal to max of previous max_len and current length, i.e, i+1
- But if it is not equal to k, check if sum-k exists in the hashmap. This means, check if there exists a sum already in the array which, if removed, will make another subarray sum to be equal to k
- if it exists, then max_len should be equal to max of previous max_len and length of subarray from index computed in previous step to i. index of previous step in already stored in hashmap
- At the end, store the current cumulative sum in hashmap with current i as value to be retrieved later to perform above steps

```py
class Solution:
    def lenOfLongSubarr (self, arr, n, k) : 
        #Complete the function
        mp={}
        max_len=0
        sums=0
        for i in range(n):
            sums+=arr[i]
            if sums==k:
                max_len=max(max_len,i+1)
            elif sums-k in mp:
                max_len=max(max_len, i-mp[sums-k])
            if sums not in mp:
                mp[sums]=i
        return max_len
```

## Intuition - Optimal approach using two pointers

Could not test this as no problem with only positives

> Time complexity - O(2n) inner while will run max for n times in whole program run

> Space complexity - O(1)

- Loop through array using i
- keep a cumulative sum of elements up to i
- if sum == k, then max_len should be equal to max of previous max_len and current length, i.e, i+1
- Otherwise, we need to move to next i. But before that, check if sums is greater than k. If yes, keep removing element from j from sum until it is smaller than k.
- At the end, return max_len

```py
class Solution:
    def lenOfLongSubarr (self, arr, n, k):
        max_len=0
        sums=0
        j=0
        for i in range(n):
            sums+=arr[i]
            if sums==k:
                max_len=max(max_len,i-j+1)
            while j<i and  sums>k:
                sums-=arr[j]
                j+=1
        return max_len
```

# With positives, negatives and zeros

## Intuition - Optimal

> Time complexity - O(nlogn) n for loop, logn to find in hashmap

> Space complexity - O(n) for hashmap

- create a hashmap, we will store cumulative sum until i as key, and i as value, in hashmap
- Loop through array using i
- keep a cumulative sum of elements up to i
- if sum == k, then max_len should be equal to max of previous max_len and current length, i.e, i+1
- But if it is not equal to k, check if sum-k exists in the hashmap. This means, check if there exists a sum already in the array which, if removed, will make another subarray sum to be equal to k
- if it exists, then max_len should be equal to max of previous max_len and length of subarray from index computed in previous step to i. index of previous step in already stored in hashmap
- At the end, store the current cumulative sum in hashmap with current i as value to be retrieved later to perform above steps

```py
class Solution:
    def lenOfLongSubarr (self, arr, n, k) : 
        #Complete the function
        mp={}
        max_len=0
        sums=0
        for i in range(n):
            sums+=arr[i]
            if sums==k:
                max_len=max(max_len,i+1)
            elif sums-k in mp:
                max_len=max(max_len, i-mp[sums-k])
            if sums not in mp:
                mp[sums]=i
        return max_len
```