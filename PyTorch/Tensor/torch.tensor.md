**Tensor**는 array이나 matrix와 매우 유사한 특수한 자료구조
Tensor ≈ Numpy ndarray

```python
import torch
import numpy as np
```

***
### Tensor Initialization

**Data to Tensor**

```python
data = [[1,2], [3,4]]
x_data = torch.tensor(data)
```

**NumPy to Tensor**

```python
np_array = np.array(data)
x_nap = torch.from_numpy(np_array)
```

**다른 텐서로부터 생성하기**
- 명시적으로 재정의(override)하지 않는다면, 인자로 주어진 텐서의 속성 (shape, datatype)을 유지한다.

```python
x_ones = torch.ones_like(x_data)  # maintain the attribute of x_data
print(f"Ones Tensor: \n {x_ones} \n")

x_rand = torch.rand_like(x_data, dtype=torch.float)  # overwrite the attribute of x_data
print(f"Random Tensor: \n {x_rand} \n")
```
```
Ones Tensor:
 tensor([[1, 1],
        [1, 1]])

Random Tensor:
 tensor([[0.4581, 0.3296],
        [0.4281, 0.0805]])
```

**Using random variable or constant value**
- shape는 dimension을 결정하는 [[tuple]]로, 아래 함수들에서는 출력 텐서의 차원을 결정한다. 

```python
shape = (2,3,)
rand_tensor = torch.rand(shape)
ones_tensor = torch.ones(shape)
zeros_tensor = torch.zeros(shape)

print(f"Random Tensor: \n {rand_tensor} \n")
print(f"Ones Tensor: \n {ones_tensor} \n")
print(f"Zeros Tensor: \n {zeros_tensor}")
```
```
Random Tensor:
 tensor([[0.1475, 0.9391, 0.0614],
        [0.0717, 0.5464, 0.1084]])

Ones Tensor:
 tensor([[1., 1., 1.],
        [1., 1., 1.]])

Zeros Tensor:
 tensor([[0., 0., 0.],
        [0., 0., 0.]])
```

**Attrubute of tensor**
```python
tensor = torch.rand(3, 4)

print(f"Shape of tensor: {tensor.shape}")
print(f"Datatype of tensor: {tensor.dtype}")
print(f"Device tensor is stored on: {tensor.device}")
```
```
Shape of tensor: torch.Size([3, 4])
Datatype of tensor: torch.float32
Device tensor is stored on: cpu
```

***
### Tensor Operation

**indexing and slicing**
```python
tensor = torch.ones(4, 4)
tensor[:,1] = 0
print(tensor)
```
```
tensor([[1., 0., 1., 1.],
        [1., 0., 1., 1.],
        [1., 0., 1., 1.],
        [1., 0., 1., 1.]])
```

**Adding (Concatenation)**
```python
t1 = torch.cat([tensor, tensor, tensor], dim=1)
print(t1)
```
```
tensor([[1., 0., 1., 1., 1., 0., 1., 1., 1., 0., 1., 1.],
        [1., 0., 1., 1., 1., 0., 1., 1., 1., 0., 1., 1.],
        [1., 0., 1., 1., 1., 0., 1., 1., 1., 0., 1., 1.],
        [1., 0., 1., 1., 1., 0., 1., 1., 1., 0., 1., 1.]])
```

**Element-wise product**
```python
# element-wise product
print(f"tensor.mul(tensor) \n {tensor.mul(tensor)} \n")

# alter
print(f"tensor * tensor \n {tensor * tensor}*")
```
```
tensor.mul(tensor)
 tensor([[1., 0., 1., 1.],
        [1., 0., 1., 1.],
        [1., 0., 1., 1.],
        [1., 0., 1., 1.]])

tensor * tensor
 tensor([[1., 0., 1., 1.],
        [1., 0., 1., 1.],
        [1., 0., 1., 1.],
        [1., 0., 1., 1.]])
```

**Matrix Multiplication**
```python
print(f"tensor.matmul(tensor.T) \n {tensor.matmul(tensor.T)} \n")
# alter
print(f"tensor @ tensor.T \n {tensor @ tensor.T}")
```
```
tensor.matmul(tensor.T)
 tensor([[3., 3., 3., 3.],
        [3., 3., 3., 3.],
        [3., 3., 3., 3.],
        [3., 3., 3., 3.]])

tensor @ tensor.T
 tensor([[3., 3., 3., 3.],
        [3., 3., 3., 3.],
        [3., 3., 3., 3.],
        [3., 3., 3., 3.]])
```

**in-place (바꿔치기) operation**
- _ 접미사를 갖는 연산들은 in-place opeation이다. x.copy_() or x.t_()는 x 자체를 변경한다.
- 메모리 근검절약할때 쓰는 방법이지만 권장은 X
```python
print(tensor, "\n")
tensor.add_(5)
print(tensor)
```
```
tensor([[1., 0., 1., 1.],
        [1., 0., 1., 1.],
        [1., 0., 1., 1.],
        [1., 0., 1., 1.]])

tensor([[6., 5., 6., 6.],
        [6., 5., 6., 6.],
        [6., 5., 6., 6.],
        [6., 5., 6., 6.]])
```