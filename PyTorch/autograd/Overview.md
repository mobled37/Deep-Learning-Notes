$n$개의 데이터 $x_1 , ... , x_n$이 주어졌다고 할때 다음의 함수 $f$를 정의할 수 있다.
$$y=f(\beta)=\frac{1}{n} \sum_{i=1}^n\left(x_i-\beta\right)^2$$
### 기울기 계산 - w/o Autograd
$$\begin{aligned}
f^{\prime}(\beta) & =\frac{d}{d \beta}\left(\frac{1}{n} \sum_{i=1}^n\left(x_i-\beta\right)^2\right) \\
& =\frac{1}{n} \sum_{i=1}^n \frac{d}{d \beta}\left(x_i-\beta\right)^2 \\
& =-\frac{1}{n} \sum_{i=1}^n 2\left(x_i-\beta\right)
\end{aligned}$$

```python
beta = torch.rand(1, requires_grad=True)    # tensor([0.7837], requires_grad=True)
y = torch.mean((data - beta) ** 2)    # tensor(11.8199, grad_fn=<MeanBackward0>)

answer = - torch.mean(2 * (data - beta))    # -5.115611
```

기울기 값을 추적할 텐서를 선언할 때 `requires_grad = True` 옵션을 선언하면 된다.
이와 관련하여 생성되는 모든 텐서에 기울기 추적 옵션 `grad_fn` 태그가 달려서 생성된다. (beta에 태그가 달려있음)
### 기울기 계산 - w Autograd

Autograd는 위 과정들을 자동으로 해준다. 기울기 값 계산을 위해서 해야 할 일은 기울기 계산을 activate 해주는 함수를 실행시켜주기만 하면 된다. `y`에 대한 베타의 기울기 값을 구하는 것으로, `.backward()`를 이용하여 backward propagation을 진행한다.
```python
y.backward()
beta.grad.item()    # -5.115611, 동일하다.
```

**.detach_()**
필요가 없어지면 기울기 자동 추적기능을 해제해야 메모리 효율적으로 모델을 돌릴 수 있다.