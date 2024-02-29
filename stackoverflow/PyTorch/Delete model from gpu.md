
**Normal Way**
- Freeing memory in PyTorch works as it does with the normal python garbage collector (import gc). This means once all references to an *python-object* are gone it will be deleted.
```python
del model
```

**if `del model` doesn't work, do this**
```python
model = network().cuda()

del model

# if model still be on cache
import gc
gc.collect()
torch.cuda.empty_cache()
```

It make sence when 