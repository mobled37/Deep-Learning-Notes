CPU 강제 지정 방법 (command line에서 처리)

```bash
# in the sh file, we address command line
taskset -c 18-35 \
python -m torch.distributed.run \
...
```

