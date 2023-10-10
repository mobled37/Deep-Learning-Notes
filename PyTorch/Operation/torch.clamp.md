reference = https://pytorch.org/docs/stable/generated/torch.clamp.html

```python
torch.clamp(input, min=None, max=None, *, out=None) -> Tensor
```

Clamps all elements in `input` into the range \[`min`, `max`\]. Letting min_value and max_value be `min` and `max`, respectively, this returns
$$y_i=\min \left(\max \left(x_i, \min \_ \mathrm {value }_i\right), \mathrm { max_value }{ }_i\right)$$
- If `min` is `None`, there is no lower bound. Or, if `max` is `None`, there is no upper bound.

> If `min` is greater than `max`, `torch.clamp(..., min, max)` sets all elements in `input` to the value of `max`

**Parameters**
* **input** ([[torch.tensor]]) - the input tensor.
* min (Number or tensor, optional) - lower-bound of the range to be clamped to
* max (Number or tensor, optional) - upper-bound of the range to be clamped to

**Keyword Arguments**
- out (tensor, optional) - the output tensor

```python
>>> a = torch.randn(4)
>>> a
# tensor([-1.7120,  0.1734, -0.0478, -0.0922])
>>> torch.clamp(a, min=-0.5, max=0.5)
# tensor([-0.5000,  0.1734, -0.0478, -0.0922])

>>> min = torch.linspace(-1, 1, steps=4)
>>> torch.clamp(a, min=min)
# tensor([-1.0000,  0.1734,  0.3333,  1.0000])
```
