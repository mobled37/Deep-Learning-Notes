Python에서 method는 크게 1. instance method, 2. static method, 3. class method가 있다. 가장 흔히 쓰이는 instance method는 instance variable에 엑세스할 수 있도록 method의 첫번째 파라미터에 항상 객체 자신을 의미하는 "self" parameter를 갖는다. 

아래 예제에서 calcArea()가 instance method에 해당된다. ==instance method의 첫번째 파라미터는 항상 self를 갖는다.== (calcArea(self)) 

```python
class Rectangle:
    count = 0
	
	# initializer (생성자)
	def __init__(self, width, height):
		# self.*: instance variable
		self.width = width
		self.height = height
		Rectangle.count += 1

	def calcArea(self):
		area = self.width * self.height
		return area
```

***
### class variable
method 밖에 존재하는 변수를 class variable이라고 하는데, 이는 해당 클래스를 사용하는 모두에게 공용으로 사용되는 변수이다. class variable은 내외부에서 "클래스명.변수명"으로 엑세스 할 수 있다. 위 예제에서 cound = class variable로서 Rectangle.count로 접근할 수 있다.

***
### instance variable
하나의 class로부터 여러 객체 instance를 생성해서 사용할 수 있다. class variable이 하나의 class에 하나만 존재하는 반면, instance variable은 각 객체 인스턴스마다 별도로 존재한다. 

method안의 "self.변수명"으로 사용되는 변수를 instance variable이라고 하는데, 이는 각 객체별로 서로 다른 값을 갖는 변수이다. instance variable은 self.width와 같이 "self."을 사용하여 엑세스하고, 클래스 밖에서는 "객체변수.인스턴스변수"와 같이 엑세스한다. 

python 코딩 관례상 내부적으로만 사용하는 variable 혹은 method는 그 이름 앞에 하나의 밑줄 (\_)를 붙인다. 만약 특정 변수명이나 메서드를 private으로 만들어야 한다면 두개의 밑줄(\_\_)을 이름앞에 붙인다. 

```python
class Rectangle:
    count = 0
	
	# initializer (생성자)
	def __init__(self, width, height):
		# self.*: instance variable
		self.width = width
		self.height = height
		Rectangle.count += 1

		# private variable = __area
		self.__area = width * height

	def calcArea(self):
		area = self.width * self.height
		return area

	# private method
	def __internalRun(self):
		pass
```

***
### initializer
class로부터 새 객체를 생성할 때마다 실행되는 특별한 method인 __init__()이라는 method가 있는데, 이를 흔히 class initializer라 부른다. python에서 두개의 밑줄로 시작하고 두개의 밑줄로 끝나는 레이블은 보통 특별 method이다. (\_\_init()\_\_)

==initializer는 class로부터 객체를 만들 때 instance variable을 initialize를 하거나 객체의 초기상태를 만들기 위한 문장들을 실행하는 곳==이다. 위의 \_\_init\_\_() 예제를 보면 width, height라는 입력 파라미터들을 각각 self.width, self.height라는 instance variable에 할당하여 객체 내에서 계속 사용할 수 있도록 준비하고 있다. 

***
### static method, class method
instance method가 객체의 인스턴스 필드를 self를 통해 엑세스할 수 있는 반면, ==static method는 이러한 self 파라미터를 갖지 않고 instance variable에 엑세스할 수 없다.== 따라서, static method는 보통 객체 필드와 독립적이지만 로직상 클래스내에 포함되는 메서트에 사용된다. static method는 method 앞에 @staticmethod라는 decorator를 표시하여 해당 method가 static method임을 표기한다. 

유사하게, class method도 @classmethod라는 decorator를 표기하여 class method임을 표시한다. ==class method는 static method와 비슷한데, 객체 instance를 의미하는 self 대신 cls라는 class를 의미하는 파라미터를 전달받는다.== class method는 이렇게 전달받은 cls 파라미터를 통해 class variable에 접근할 수 있다.

==일반적으로, instance data에 엑세스할 필요가 없는 경우 class method, static method를 이용하는데, 이때 보통 class variable에 접근해야하는 경우에는 class method, 접근이 필요 없는 경우에는 static method를 사용한다.== 

아래 예제에서 isSquare() method는 static method로서 cls 파라미터를 전달받지 않고 매서드 내에서 cls 변수를 사용하지 않고 있다. 반면, printCount() method는 class method로서 cls 파라미터를 전달받고 메서드 내에서 class variable count를 사용하고 있다.

```python
class Rectangle:
	count = 0 # cls variable

	def __init__(self, width, height):
		self.width = width
		self.height = height
		Rectangle.count += 1 

	# instance method
	def calcArea(self):
		area = self.width * self.height
		return area

	# static method
	@staticmethod
	def isSquare(rectWidth, rectHeight):
		return rectWidth == rectHeight

	# class method
	@classmethod
	def printCount(cls):
		print(cls.count)

square = Rectangle.isSquare(5, 5)
print(square)

rect1 = Rectangle(5,5)
rect2 = Rectangle(2,5)
rect1.printCount() # 2
```

