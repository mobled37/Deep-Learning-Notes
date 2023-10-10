reference = https://pytorch.org/docs/stable/generated/torch.nn.utils.clip_grad_norm_.html

```python
torch.nn.utils.clip_grad_norm_(parameters, max_norm, norm_type=2.0, error_if_nonfinite=False, foreach=None)
```

Clips gradient norm of an iterable of parameters

The norm is computed over all gradients together, as itf they were concatenated into a single vector. Gradients are modified in-place.

- **parameters** (_Iterable_ [_[[Tensor]]_]or [_Tensor_] – an iterable of Tensors or a single Tensor that will have gradients normalized
    
- **max_norm** ([_float_](https://docs.python.org/3/library/functions.html#float "(in Python v3.11)")) – max norm of the gradients
    
- **norm_type** ([_float_](https://docs.python.org/3/library/functions.html#float "(in Python v3.11)")) – type of the used p-norm. Can be `'inf'` for infinity norm.
    
- **error_if_nonfinite** ([_bool_](https://docs.python.org/3/library/functions.html#bool "(in Python v3.11)")) – if True, an error is thrown if the total norm of the gradients from `parameters` is `nan`, `inf`, or `-inf`. Default: False (will switch to True in the future)
    
- **foreach** ([_bool_](https://docs.python.org/3/library/functions.html#bool "(in Python v3.11)")) – use the faster foreach-based implementation. If `None`, use the foreach implementation for CUDA and CPU native tensors and silently fall back to the slow implementation for other device types. Default: `None`