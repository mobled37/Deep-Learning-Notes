```python
tensor.masked_fill_(mask, value)
```
- mask (BoolTensor) - the boolean mask
- value (float) - the value to fill in with

Fills elements of **self** tensor with **value** where **mask** is True. The shape of **mask** must be broadcastable with the shape of the underlying tensor.

***
**Example**
```python
# in the HBI
text_weight.masked_fill_(torch.tensor((1-text_mask), dtype=torch.bool), float(-9e15))
```

```python
import torch
from torch import nn 

text = torch.tensor([[4,4], [4,4]])
text_mask = torch.tensor([[1,0], [0,1]])

text.masked_fill_(torch.tensor((1-text_mask), dtype=torch.bool), float(-9e15))
print(text)
```
```
tensor([[ 4, -9000000000000000], 
        [-9000000000000000, 4]])
```
```python
text.masked_fill_(torch.tensor((text_mask), dtype=torch.bool), float(-9e15))
print(text)
```
```
tensor([[-9000000000000000, 4], 
        [4, -9000000000000000]])
```
