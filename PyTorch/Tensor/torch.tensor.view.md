reference = https://pytorch.org/docs/stable/generated/torch.Tensor.view.html

[[torch.tensor]].view(\*shape) -> Tensor
==Returns a new tensor with the same data as the **self** tensor but of a different **shape**==

The returned tensor shares the **same data, same number of elements** but **different size**.

For a tensor to be viewed, the new view size must be compatible with its original size and stride or only span across original dimensions $d, d+1, ... , d+k$ that satisfy the following contiguity-like condition that $\forall i=d, \ldots, d+k-1$ 
$$\operatorname{stride}[i]=\operatorname{stride}[i+1] \times \operatorname{size}[i+1]$$
+) When it is unclear whether a view() can be performed, it is advisable to use reshape(), which returns a view if the shapes are compatible, and copies (equivalent to calling [[torch.tensor.contiguous]]()) otherwise.

```python
>>> x = torch.randn(4, 4)
>>> x.size()
# torch.Size([4, 4])
>>> y = x.view(16)
>>> y.size()
# torch.Size([16])
>>> z = x.view(-1, 8)  # the size -1 is inferred from other dimensions
>>> z.size()
# torch.Size([2, 8])

>>> a = torch.randn(1, 2, 3, 4)
>>> a.size()
# torch.Size([1, 2, 3, 4])
>>> b = a.transpose(1, 2)  # Swaps 2nd and 3rd dimension
>>> b.size()
# torch.Size([1, 3, 2, 4])
>>> c = a.view(1, 3, 2, 4)  # Does not change tensor layout in memory
>>> c.size()
# torch.Size([1, 3, 2, 4])
>>> torch.equal(b, c)
# False
```

