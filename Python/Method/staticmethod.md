
staticmethod (정적 메서드)는 method위에 @staticmethod를 붙인다. 이때 staticmethod는 variable로 self를 지정하지 않는다.
```python
class classname:
	@staticmethod
	def method(var1, var2):
		code
```

@staticmethod 처럼 @이 붙은 것을 decorator라고하며 method (function)에 추가 기능을 구현할 때 사용한다.
staticmethod를 호출할 때는 다음과 같이 클래스에서 바로 function을 호출하면 된다. 
```python
class Calc:
	@staticmethod
	def add(a, b):
		print(a + b)

	@staticmethod
	def mul(a, b):
		print(a * b)

Calc.add(10, 20) # 클래스에서 바로 function 호출
Calc.mul(10, 20) # 클래스에서 바로 function 호출
```

@staticmethod는 self를 받지 않으므로 instance property에는 접근할 수 없다. 따라서 보통 staticmethod는 instance property, instance method가 필요 없을 때 사용한다. 
staticmethod는 instance의 상태를 변화시키지 않는 function을 만들 때 사용한다. 

**참고** 파이썬 자료형의 instance method와 static method
파이썬의 자료형도 instance method와 static, class method로 나뉘어져 있다. 예를 들어 세트에 요소를 더할 때는 instance method를 사용하고, 합집합을 구할 때는 static method를 사용하도록 만들어져 있다. 
```python
>>> a = {1, 2, 3, 4}
>>> a.update({5})    # 인스턴스 메서드
>>> a
{1, 2, 3, 4, 5}
>>> set.union({1, 2, 3, 4}, {5})    # 정적(클래스) 메서드
{1, 2, 3, 4, 5}
```

이처럼, 인스턴스의 내용을 변경해야 할 때는 update와 같이 instance method로 작성하면 되고, instance 내용과는 상관없이 결과만 구하면 될 때는 set.union과 같이 정적 메서드로 작성하면 된다.