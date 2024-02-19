- `torch.nn.Fold(output_size, kernel_size, dilation=1, padding=0, stride=1)`

Combining an array of sliding local blocks into a large containing tensor.

Consider a batched `input` tensor containing sliding local blocks, e.g., patches of images, of shape ($N, C \times \prod(\mathrm{kernel\_size}), L$), where $N$ is batch dimension, $C \times \prod(\mathrm{kernel\_size})$ is the number of values within a block (a block has $\prod(\mathrm{kernel\_size})$ spatial locations each containing a $C$-channeled vector), and $L$ is the total number of blocks. (This is exactly the same specification as the output shape of `Unfold`.) This operation 