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
	for i in 
```