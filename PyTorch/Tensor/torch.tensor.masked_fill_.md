```python
tensor.masked_fill_(mask, value)
```
- mask (BoolTensor) - the boolean mask
- value (float) - the value to fill in with

Fills elements of **self** tensor with **value** where **mask** is True. The shape of **mask** must be broadcastable with the shape of the underlying tensor.

Example
```python
# in the HBI
text_weight.masked_fill_(torch.tensor((1-text_mask), dtype=torch.bool), float(-9e15))
```