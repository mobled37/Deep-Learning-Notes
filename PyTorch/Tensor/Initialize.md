torch.nn.init

|nonlinearity|gain|
|---|---|
|linear/Identity|1|
|Conv{1,2,3}D|1|
|Sigmoid|1|
|Tanh|5/3|
|ReLU|$\sqrt{2}$|
|Leaky Relu|$\sqrt{\frac{2}{1+\mathrm {negative_slope}^2}}$|
|SELU|3/4|

**torch.nn.init.xavier_normal_(tensor, gain=1.0)**
Fills the input *tensor* with values according to the method described in *Understanding the difficulty of training deep feedforward neural networks* - Glorot, X. & Bengio, Y. (2010), using a normal distribution.
The resulting tensor will have values sampled from $\mathcal{N}(0, \mathrm{std}^2)$ where 
$$\mathrm{std} = \mathrm{gain} \times \sqrt{2 \over \mathrm{fan \_ in} + {\mathrm{fan\_ out}}}$$
Also known as ***Glorot initalization***