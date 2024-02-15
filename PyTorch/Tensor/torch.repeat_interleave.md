`torch.repeat_interleave(input, repeats, dim=None, *, output_size=None) -> Tensor`
- repeat elements of a tensor.

Warning
- This is different from `torch.Tensor.repeat()` but similar to `numpy.repeat`.

**Parameters**
- **input** ([[torch.tensor]]) - the input tensor
- **repeats** ([[torch.tensor]] or [[int]]) - The number of repetitions for each element. repeats is broadcasted to fit the shape of the given axis.
- **dim** ([[int]], optional) - The dimension along which to repeat values. By default, use the flattened input array, and return a flat output array. 

**Keyword Arguments**
- **output_size** ([[int]], optional) - Total output size for the given axis (e.g. sum of repeats). If given, it will avoid stream synchronization needed to calculate output shape of the tensor.

**Returns**
- Repeated tensor which has the same shape as input, except along the given axis.

**Return type**
* [[torch.tensor]]

**Example**