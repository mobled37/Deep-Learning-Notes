`Class torch.Generator(device='cpu')`

Creates and returns a generator object that manages the state of the algorithm which produces pseudo random numbers. Used as a keyword argument in many In-place random sampling functions.

Parameters

**device** ([`torch.device`](https://pytorch.org/docs/stable/tensor_attributes.html#torch.device "torch.device"), optional) – the desired device for the generator.

Returns

An torch.Generator object.

Return type

[[torch.Generator]] 

```python
>>> g_cpu = torch.Generator()
>>> g_cuda = torch.Generator(device='cuda')
```

***
**device**

Generator.device -> device

Gets the current device of the generator.

Example:
```python
>>> g_cpu = torch.Generator()
>>> g_cpu.device
device(type='cpu')
```

***
get_state() → [[torch.tensor]]

Returns the Generator state as a `torch.ByteTensor`.

Returns

A `torch.ByteTensor` which contains all the necessary bits to restore a Generator to a specific point in time.

Return type

[[torch.tensor]]

Example:
```python
>>> g_cpu = torch.Generator()
>>> g_cpu.get_state()
```

***
initial_seed() → [[int]]

Returns the initial seed for generating random numbers.

Example:
```python
>>> g_cpu = torch.Generator()
>>> g_cpu.initial_seed()
# 2147483647
```

***
manual_seed(_seed_) → [[torch.Generator]]

Sets the seed for generating random numbers. Returns a torch.Generator object. Any 32-bit integer is a valid seed.

Parameters

**seed** ([_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.12)")) – The desired seed. Value must be within the inclusive range \[-0x8000_0000_0000_0000, 0xffff_ffff_ffff_ffff\]. Otherwise, a RuntimeError is raised. Negative inputs are remapped to positive values with the formula 0xffff_ffff_ffff_ffff + seed.

Returns

An torch.Generator object.

Return type

[[torch.Generator]]

Example:
```python
>>> g_cpu = torch.Generator()
>>> g_cpu.manual_seed(2147483647)
```
seed() → [int](https://docs.python.org/3/library/functions.html#int "(in Python v3.12)")[](https://pytorch.org/docs/stable/generated/torch.Generator.html#torch.Generator.seed)

Gets a non-deterministic random number from std::random_device or the current time and uses it to seed a Generator.

Example:

>>> g_cpu = torch.Generator()
>>> g_cpu.seed()
1516516984916

set_state(_new_state_) → void[](https://pytorch.org/docs/stable/generated/torch.Generator.html#torch.Generator.set_state)

Sets the Generator state.

Parameters

**new_state** (_torch.ByteTensor_) – The desired state.

Example:

>>> g_cpu = torch.Generator()
>>> g_cpu_other = torch.Generator()
>>> g_cpu.set_state(g_cpu_other.get_state())