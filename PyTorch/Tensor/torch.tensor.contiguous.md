![[Pasted image 20231005151056.png]]

b는 axis = 0 인 오른쪽 방향으로 자료가 순서대로 저장됨에 비해,
a는 transpose 연산을 거치며 axis = 1인 아래 방향으로 자료가 저장되고 있다.

여기서, b처럼 axis 순서대로 자료가 저장된 상태를 contiguous = True, a처럼 자료 저장 순서가 원래 방향과 어긋난 경우를 contiguous = False 상태라고 한다. 

주로 narrow(), view(), expand(), transpose() 등 메소드를 사용하는 경우에 이 상태가 깨진다. 
만일 RuntimeError: input is not contiguous 오류가 발생하면 input tensor를 contiguous하게 바꿔줘야 한다. 

```python
# a is tensor
a.is_contiguous()  # False

a = a.congtiguous()

a.is_contiguous()  # True
```
