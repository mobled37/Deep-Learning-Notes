Reference: https://pytorch.org/docs/stable/generated/torch.nn.Softmax.html

```python
torch.softmax(dim=None)
```

Applies the softmax function to an n-dimensional input Tensor rescaling them so that the elements of the n-dimensional ouput tensor lie in the range [0,1] and sum to 1. 
$$\operatorname{Softmax}\left(x_i\right)=\frac{\exp \left(x_i\right)}{\sum_j \exp \left(x_j\right)}$$
* input: (\*) where \* means, any number of additional dimensions
* output: (\*), same shape as the input

**Returns**
- a tensor of the same dimension and shape as the input with values in the range [0, 1]

**Parameters**
- **dim** (int) - A dimension along which Softmax will be computed (so every slice along dim will sum to 1)

**Return type**
- None

### Example
```python
>>> m = torch.softmax(dim=1)
>>> input = torch.randn(2,3)
>>> output = m(input)
```

```python
# in the HBI
video_weight = torch.softmax(video_weight, dim=-1)
```
