reference = https://pytorch.org/docs/stable/autograd.html

```python
torch.autograd.detect_anomaly(check_nan=True)
```

Context-manager that enable anomaly detection for the autograd engine. This does two things:
- Running the forward pass with detection enabled will allow the backward pass to ==print the traceback of the forward operation== that created the failing backward function. 
==- If check_nan is True, any backward computation that generate "nan" value will raise an error.== 

Example
```python
with torch.autograd.detect_anomaly():
	loss.backward()
```