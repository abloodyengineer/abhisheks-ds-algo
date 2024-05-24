# Remove duplicates from sorted array

[Problem link - Leetcode](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/){:target="_blank"}


## Intuition

- initialize largest1 and largest2
- Loop through array
- if you get an element greater than largest1, make largest2 = largest 1 now, and largest1 = arr[i]
- else, if element is greater than largest2, make largest2=arr[i]

```py
class Solution:
	def print2largest(self,arr, n):
		# code here
		largest1=arr[0]
	    largest2=-1
	    for i in range(1,n):
            if arr[i]>largest1:
                largest2=largest1
                largest1=arr[i]
            elif arr[i]<largest1 and arr[i]>largest2:
                largest2=arr[i]
	    return largest2
```