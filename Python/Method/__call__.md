
**Stack Overflow**
The first is used to initialise newly created object, and receives arguments used to do that:
- 
```python
class Foo:
	def __init__(self, a, b, c):
		# ...

x = Foo(1, 2, 3) # __init__
```

The second implements function call operator
```python
class Foo:
	def __call__(self, a, b, c):
		# ...

x = Foo()
x(1, 2, 3)
```