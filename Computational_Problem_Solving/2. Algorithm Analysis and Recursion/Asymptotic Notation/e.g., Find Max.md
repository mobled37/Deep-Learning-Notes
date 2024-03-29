
```python
def findMax(A):
	largest = A[0]
	for val in A:
		if val > largest:
			largest = val
	return largest
```

- The number of instructions in findMax: $c_1 + c_2n$
* Time complexity: $\Theta(n)$ 
