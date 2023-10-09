reference = https://tutorials.pytorch.kr/beginner/examples_autograd/polynomial_custom_function.html

$y = \sin (x)$ 를 예측할 수 있도록, $-\pi$ 부터 $\pi$ 까지 Euclidean distance를 최소화하도록 3차 다항식을 학습하는 예제입니다. $y = a+bx+cx^2+dx^3$를 $y=a+bP_3(c+dx)$로 다항식을 적겠습니다. 여기서 $P_3(x)=(5x^3-3x)/2$ 입니다.

이 예제는 PyTorch Tensor Operation을 이용하여 forward pass (순전파)를 계산하고, PyTorch autograd를 사용하여 gradient(변화도)를 계산한다. 

이 예제에서는 $P'_3(x)$를 수행하기 위해 사용자 정의 autograd Function을 구현한다. 수학적으로는 $P'_3(x)=3(5x^2-1)/2$이다.

```python
import torch
import math

class LegendrePolynomial3(torch.autograd.Function):
	"""
	torch.autograd.Function을 상속받아 사용자 정의 autograd Function을 구현하고, 
	텐서 연산을 하는 순전파 단계와 역전파 단계를 구현한다.
	"""
	@staticmethod
	def forward(ctx, input):
		"""
		순전파 단계에서는 입력을 갖는 텐서를 받아 출력을 갖는 텐서를 반환한다.
		ctx는 context object로 역전파 연산을 위한 정보 저장에 사용한다.
		ctx.save_for_backward method를 사용하여 역전파 단계에서 사용할
		어떤 객체도 저장(cache) 해놓을 수 있다. 
		"""
		ctx.save_for_backward(input)
		return 0.5 * (5 * input ** 3 - 3 * input)
	@staticmethod
	def backward(ctx, grad_output):
		"""
		역전파 단계에서는 출력에 대한 손실(loss)의 변화도(gradient)를 갖는 텐서를 받고,
		입력에 대한 손실과 변화도를 계산해야한다.
		"""
		input, = ctx.saved_tensor
		return grad_output * 1.5 * (5 * input ** 2 -1)

dtype = torch.float
device = torch.device("cpu")

"""
입력값과 출력값을 갖는 텐서들을 생성한다.
requires_grad=False가 기본값으로 설정되어 Backpropagation 중에 이 텐서들에 대한
gradient를 계산할 필요가 없음을 나타낸다.
"""
x = torch.linspace(-math.pi, math.pi, 2000, device=device, dtype=dtype)
y = torch.sin(x)

"""
가중치를 갖는 임의의 텐서를 생성한다. 3차 다항식이므로 4개의 가중치가 필요하다.
y = a + b * P3(c + d * x) 
이 가중치들이 convergence하기 위해서는 정답으로부터 너무 멀리 떨어지지 않은 값으로
initialize 되어야 한다.
requires_grad=True로 설정하여 backprop 중에 이 tensor들에 관한 gradient를 계산할
필요가 있음을 나타낸다.
"""
a = torch.full((), 0.0, device=device, dtype=dtype, requires_grad=True)
b = torch.full((), -1.0, device=device, dtype=dtype, requires_grad=True)
c = torch.full((), 0.0, device=device, dtype=dtype, requires_grad=True)
d = torch.full((), 0.3, device=device, dtype=dtype, requires_grad=True)

learning_rate = 5e-6
for t in range(2000):
	""" 사용자 정의 Function을 적용하기 위해 Function.apply method를 사용한다. """
	P3 = LegendrePolynomial3.apply
	
	"""
	forward pass: 연산을 하여 예측값 y를 계산한다
	사용자 정의 autograd 연산을 사용하여 P3를 계산한다.
	"""
	y_pred = a + b * P3(c + d * x)
	
	loss = (y_pred - y).pow(2).sum()
	if t % 100 == 99:
		print(t, loss.item())
	
	""" autograd를 사용하여 backprop을 계산한다 """
	loss.backward()
	
	""" gradient descent를 사용하여 weight를 update """
	with torch.no_grad():
		a -= learning_rate * a.grad
		b -= learning_rate * b.grad
		c -= learning_rate * c.grad
		d -= learning_rate * d.grad
		
		""" weight update 이후에는 gradient를 0으로 만든다 """
		a.grad = None
		b.grad = None
		c.grad = None
		d.grad = None
```