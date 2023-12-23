Tests if each element of `input` is infinite (positive or negative infinity) or not

```python
>>> torch.isinf(torch.tensor([1, float('inf'), 2, float('-inf'), float('nan')]))
```
```
tensor([False, True, False, True, False])
```