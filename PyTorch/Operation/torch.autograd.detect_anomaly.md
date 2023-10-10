```python
torch.autograd.detect_anomaly(check_nan=True)
```

Context-manager that enable anomaly detection for the autograd engine. This does two things:
- Running the forward pass with detection enabled will allow the backward pass to print the traceback of the forward operation that created the failing backward function. 