- A recursion where **the recursive call is the final instruction** in the recursive function
- There should be only one recursive call in the function

C++ function print() is tail recursive
```python
def prints(n):
	if (n < 0):
		return
	print(str(n), end=" ")

	# The last excuted statement is recursive call
	prints(n - 1)

# Time complexity: O(n)
# Auxiliary Space: O(n)
```

**Benefits of Tail Recursion**


- The tail recursive functions are considered better than non-tail recursive functions as **tail-recursion can be optimized by the compiler.**
	- Avoid the accumulation of stack overheads during the recursive calls
	- 


--------
references
- [tail recursion](https://www.geeksforgeeks.org/tail-recursion/)
- 
