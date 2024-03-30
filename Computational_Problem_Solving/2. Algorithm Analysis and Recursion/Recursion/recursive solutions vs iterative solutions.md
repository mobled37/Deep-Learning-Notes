Recursive algorithms can be space-inefficient.
- Each recursive call adds a new layer to the stack = if algorithm recurses to a depth of n, it uses at least $O(n)$ space.

Implementing recursive algorithms iteratively is more complex.
**All recursive algorithms can be implemented iteratively.**

**Example:** Fibonacci Sequence

**Recursion (inefficient)**
```python
def fibonacci(n):
	if n == 0 or n == 1:
		return n
	else:
		return fibonacci(n - 1) + fibonacci(n - 2)
```

**Iterative (efficient)**
```python
def fibonacci(n):
	# base case (0 and 1)
	if n == 0:
		return 0
	elif n == 1:
		return 1

	a, b = 0, 1
	for _ in range(2, n + 1):
		c = a + b
		a, b = b, c

	return c
```

- The iterative solution is more efficient for larget values of $n$ due to the lower overhead and memory usage compared to the recursive approach.