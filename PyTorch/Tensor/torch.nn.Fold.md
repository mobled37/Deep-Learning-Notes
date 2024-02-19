- `torch.nn.Fold(output_size, kernel_size, dilation=1, padding=0, stride=1)`

Combining an array of sliding local blocks into a large containing tensor.

Consider a batched `input` tensor containing sliding local blocks, e.g., patches of images, of shape ($N, C \times \prod(\mathrm{kernel\_size}), L$), where $N$ is batch dimension, $C \times \prod(\mathrm{kernel\_size})$ is the number of values within a block (a block has $\prod(\mathrm{kernel\_size})$ spatial locations each containing a $C$-channeled vector), and $L$ is the total number of blocks. (This is exactly the same specification as the output shape of `Unfold`.) This operation combines these local blocks into the large `output` tensor of shape $(N, C, \mathrm{output\_size[0]}, \mathrm{output\_size[1]}, ...)$ by summing the overlapping values. Similar to `Unfold`, the arguments must satisfy
$$
L=\prod_d\left\lfloor\frac{\mathrm { output_size }[d]+2 \times \mathrm { padding }[d]-\mathrm { dilation }[d] \times(\mathrm { kernel_size }[d]-1)-1}{\operatorname{stride}[d]}+1\right\rfloor
$$
where $d$ is over all spatial dimensions. 

- `output_size` describes the spatial shape of the large containing tensor of the sliding local blocks. It is useful to resolve the ambiguity when multiple input shapes map to same number of sliding blocks, e.g., with `stride > 0`. 

The `padding`, `stride` and `dilation` arguments specify how the sliding blocks are retrieved. 

- `stride` controls the stride for the sliding blocks.
- `padding` cont