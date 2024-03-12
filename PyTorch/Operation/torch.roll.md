`torch.roll(input, shifts, dims=None) → Tensor`

- Roll the tensor `input` along the given dimensions. Elements that are shifted beyond the last position are re-introduced at the first position. If `dims` is *None*, the tensor will be flattened before rolling and then restored to the original shape.

**Parameters**
- **input** ([[torch.tensor]]) - the input tensor. 
- **shifts** ([[int]] or [[tuple]] of ints) - the number of places by which the elements of the tensor are shifted. If shifts is a tuple, dims must be a tuple of the same size, and each dimension will be rolled by the corresponding value.
- **dims** ([[int]] or [[tuple]] of ints) - axis along which to roll

**Example**
```python
>>> x = torch.tensor([1, 2, 3, 4, 5, 6, 7, 8]).view(4, 2)
>>> x
tensor([[1, 2],
        [3, 4],
        [5, 6],
        [7, 8]])
>>> torch.roll(x, 1)
tensor([[8, 1],
        [2, 3],
        [4, 5],
        [6, 7]])
>>> torch.roll(x, 1, 0)
tensor([[7, 8],
        [1, 2],
        [3, 4],
        [5, 6]])
>>> torch.roll(x, -1, 0)
tensor([[3, 4],
        [5, 6],
        [7, 8],
        [1, 2]])
>>> torch.roll(x, shifts=(2, 1), dims=(0, 1))
tensor([[6, 5],
        [8, 7],
        [2, 1],
        [4, 3]])
```
