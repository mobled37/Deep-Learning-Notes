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