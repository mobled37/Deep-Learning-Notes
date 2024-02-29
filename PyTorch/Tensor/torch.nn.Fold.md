- `torch.nn.Fold(output_size, kernel_size, dilation=1, padding=0, stride=1)`

********
`Unfold` example

```python
x = torch.tensor([[1, 2, 3, 4, 5], [6, 7, 8, 9, 10]])
```

```python
>>> x.unfold(1, 2, 1)

tensor([[[ 1,  2], [ 2,  3], [ 3,  4], [ 4,  5]],
        [[ 6,  7], [ 7,  8], [ 8,  9], [ 9, 10]]])

```


![image](https://i.stack.imgur.com/uCrOg.png)
This image explain `Unfold`, `fold` is step 1, 2. 
***

Combining an array of sliding local blocks into a large containing tensor.

Consider a batched `input` tensor containing sliding local blocks, e.g., patches of images, of shape ($N, C \times \prod(\mathrm{kernel\_size}), L$), where $N$ is batch dimension, $C \times \prod(\mathrm{kernel\_size})$ is the number of values within a block (a block has $\prod(\mathrm{kernel\_size})$ spatial locations each containing a $C$-channeled vector), and $L$ is the total number of blocks. (This is exactly the same specification as the output shape of `Unfold`.) This operation combines these local blocks into the large `output` tensor of shape $(N, C, \mathrm{output\_size[0]}, \mathrm{output\_size[1]}, ...)$ by summing the overlapping values. Similar to `Unfold`, the arguments must satisfy
$$
L=\prod_d\left\lfloor\frac{\mathrm { output\_size }[d]+2 \times \mathrm { padding }[d]-\mathrm { dilation }[d] \times(\mathrm { kernel\_size }[d]-1)-1}{\operatorname{stride}[d]}+1\right\rfloor
$$
where $d$ is over all spatial dimensions. 

- `output_size` describes the spatial shape of the large containing tensor of the sliding local blocks. It is useful to resolve the ambiguity when multiple input shapes map to same number of sliding blocks, e.g., with `stride > 0`. 

The `padding`, `stride` and `dilation` arguments specify how the sliding blocks are retrieved. 

- `stride` controls the stride for the sliding blocks.
- `padding` controls the amount of implicit zero-paddings on both sides for `padding` number of points for each dimension before reshaping.
- `dilation` controls the spacing between the kernel points; also known as the à trous algorithm. It is harder to describe, but [link](https://github.com/vdumoulin/conv_arithmetic/blob/master/README.md) has a nice visualization of what `dilation` does.

**Parameters**

- **output_size** ([[int]] or [[tuple]]) - the shape of the spatial dimensions of the output (i.e., `output.sizes()[2:]`)
- **kernel_size** ([[int]] or [[tuple]]) - the size of the sliding blocks
- **dilation** ([[int]] or [[tuple]], optional) - a parameter that controls the stride of elements within the neighborhood. Default: 1
- **padding** ([[int]] or [[tuple]], optional) - implicit zero padding to be added on both sides of input. Default: 0
- **stride** ([[int]] or [[tuple]]) - the stride of the sliding blocks in the input spatial dimensions. Default: 1

**Shape**: 
- Input: $(N, C \times \prod (\mathrm{kernel\_size}), L)$ or $(C \times \prod (\mathrm{kernel\_size}), L)$
- Output: $(N, C, \mathrm{output\_size[0]}, \mathrm{output\_size[1]}, ...)$ or $(C, \mathrm{output\_size[0]}, \mathrm{output\_size[1]}, ...)$ as described above.

**NOTE**
`Fold` calculates each combined value in the resulting large tensor by summing all values from all containing blocks.
`Unfold` extracts the values in the local blocks by copying from the large tensor. 
So, if the blocks overlap, they are not inverses of each other. 

In general, folding and unfolding operations are related as follows. Consider `Fold` and `Unfold` instances created with the same parameters:

```python
>>> fold_params = dict(kernel_size=..., dilation=..., padding=..., stride=...)
>>> fold = nn.Fold(output_size=..., **fold_params)
>>> unfold = nn.Unfold(**fold_params)
```

Then for any (supported) `input` tensor the following equality holds:

```python
fold(unfold(input)) == divisor * input
```

where `divisor` is a tensor that depends only on the shape and dtype of the `input`:

```python
>>> input_ones = torch.ones(input.shape, dtype=input.dtype)
>>> divisor = fold(unfold(input_ones))
```

When the `divisor` tensor contains no zero elements, then `fold` and `unfold` operations are inverses of each other (up to constant divisor).

+) Currently, only unbatched (3D) or batched (4D) image-like tensors are supported.

**Examples**

```python
>>> fold = nn.Fold(output_size=(4, 5), kernel_size=(2, 2))
>>> input = torch.randn(1, 3 * 2 * 2, 12)
>>> output = fold(input)
>>> output.size()
torch.Size([1, 3, 4, 5])
```
