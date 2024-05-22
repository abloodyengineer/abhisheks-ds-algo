# **Time Complexity**
---
The time complexity of an algorithm quantifies the amount of time taken by an algorithm to run as a function of the length of the input. Note that the time to run is a function of the length of the input and not the actual execution time of the machine on which the algorithm is running on.


# **Examples - Iterative**
---
Lets go through examples to understand the concepts.

## Example-1 | **O(n)**
---
```py
for i in range(n):
	print(i)
```

loop will run for 1+1+1+1+1+...n times = n.  
Hence O(n)

## Example-2 | **O(n^2)**
---
```py
for i in range(n):
    for j in range(n):
	    print(i)
```
Outer loop will run for 1+1+1+1+1+...n times = n  
Inner loop will run for 1+1+1+1+1+...n times = n  
As these are nested, total time = n^2  
Hence O(n^2)

## Example-3 | **O(log n)**
---
```py
index=0
size = 129
while index < size:
    print(index)
    index *= 2
```
loop will run for 1*2*2*2*2*...k times = 2^k
Complexity should be k then  
Loop will stop when 2^k >=n  
Hence, we can calculate k  
2^k=n  
k=log n  
Hence O(log n)

# **Examples - Recursive**
---
## Example-1 | **Fibonacci**

```
T(n)=k+T(n-1)  
T(n-1)=k+T(n-2)  
.  
.  
.  
T(1)=k (Base condition)
```
Adding everything above, we get   
T(n)=k*n

Hence, **O(n)**

## Example-2 | **Binary search**

```
T(n)=k+T(n/2)  
T(n/2)=k+T(n/4)  
.  
.  
.  
T(1)=k (Base condition)
```
Adding everything above, we get   
T(n)=a(number of steps)* k

Now, a= log n(which is number of steps)
Hence, T(n) = k*log n

Hence, **O(log n)**

## Example-3 | **Merge sort**

- Break into 2 arrays, left and right
- Sort using recursion
- Merge into a new array (O(kn))
- Copy new array content to original array (O(kn))

```
T(n)=k+T(n/2)+T(n/2)+kn+kn  
T(n)=2T(n/2)+kn  

2T(n/2)=4T(n/4)+kn (multiplied both side by 2)  
.  
.  
.  
T(1)=k (Base condition)
```
Adding everything above, we get   
T(n)=a(number of steps)* nk

Now, a= log n(which is number of steps)
Hence, T(n) = nk*log n

Hence, **O(nlog n)**

## Example-4 | **Fibonacci**
```
T(n)=T(n-1)+T(n-2)

Forms a binary tree with n levels

Total nodes = 1+2^1+2^2+2^3+...2^n  
Each node = k operation  

T.C = k*Total nodes  
    = k*((2^n+1)-1) [Formula]  
    =k*2^n [approx]  
```
Hence, **O(2^n)**