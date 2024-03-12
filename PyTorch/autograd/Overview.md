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

answer = - torch.mean(2 * (data - beta))
```

기울기 값을 추적할 텐서를 선언할 때 `requires_grad = True` 옵션을 선언하면 된다.
이와 관련하여 생성되는 모든 텐서에 기울기 추적 옵션 `grad_fn` 태그가 달려서 생성된다. (beta에 태그가 달려있음)
### 기울기 계산 - w Autograd
