
**Stack Overflow**
The first is used to initialise newly created object, and receives arguments used to do that:
- `__init__` is called when instantiating the class
```python
class Foo:
	def __init__(self, a, b, c):
		# ...

x = Foo(1, 2, 3) # __init__
```

The second implements function call operator
- `__call__` is a template to call the already instantiated class to do something
```python
class Foo:
	def __call__(self, a, b, c):
		# ...

x = Foo()
x(1, 2, 3)
```