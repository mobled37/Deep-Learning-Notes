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

![[tail-recursion.png]]

For the sequence of recursive calls $f(x_1) \rightarrow f(x_2) \rightarrow f(x_3), f(x)$ is implemented as tail recursion
	1. Space in the stack is allocated for $f(x_1)$ in order to call $f(x_2)$ in step 1
	2. Function $f(x_2)$ recursively calls $f(x_3)$ in step 2
	3. Function $f(x_3)$ reaches the base case, and **function simply returns the result to the first caller without going back to the previous function calls.** (순차적임)

**Examples**
```python
def sum_of_numbers_non_tail_recursion(lst: List[int]) -> int:
	# base case
	if len(lst) == 1:
		return lst[0]
	else:
		return sum_of_numbers_non_tail_recursion(lst[:-1]) + lst[-1]
```
- This function cannot be called *tail recursion*. Because, when base case, we have the operation to add `lst[0]`. 

So the fixed version
```python
def sum_of_numbers_tail_recursion(lst: List[int], total: int = 0) -> int:
	# base case
	if len(lst) == 0:
		return total
	else:
		return sum_of_numbers_tail_recursion(lst[:-1], total + lst[-1])
```
- This function can be called tail recursion because last operation is the recursion call. 

Using helper function


--------
references
- [tail recursion](https://www.geeksforgeeks.org/tail-recursion/)
- 
