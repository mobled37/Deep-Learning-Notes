python의 리스트나 튜플처럼, 클래스의 인스턴스 자체도 슬라이싱 할 수 있다.
이때 필요한 속성이 getitem 이라는 속성이다.

두개의 밑줄로 시작하는 파이썬의 특별 메소드 중 하나이다.
슬라이싱을 구현할 수 있도록 도우며 __리스트에서 슬라이싱을 하게되면 내부적으로 getitem 메소드를 실행한다.__
그렇기에, 객체에서도 슬라이싱을 하기 위해서는 getitem 메소드가 필수적이다.

```python
class CustomNumbers:
	def __init__(self):
		self._numbers = [n for n in range(1, 11)]

a = CustomNumbers()
a._numbers[2:5]
```
```
[3, 4, 5]
```

인스턴스 변수에 직접 접근하지 말고 객체 자체를 통해서 슬라이싱을 구현하기 위해서는 getitem 특별 메소드를 정의해야한다.
getitem 함수는 index를 인수로 받는다. 

```python
class CustomNumbers:
	def __init__(self):
		self._numbers = [n for n in range(1, 11)]

	def __getitem__(self, idx):
		return self._numbers[idx]

a = CustomNumbers()
a._numbers[2:5]
```
```
[3, 4, 5]
```

