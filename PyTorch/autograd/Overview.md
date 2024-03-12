$n$개의 데이터 $x_1 , ... , x_n$이 주어졌다고 할때 다음의 함수 $f$를 정의할 수 있다.
$$y=f(\beta)=\frac{1}{n} \sum_{i=1}^n\left(x_i-\beta\right)^2$$
### 기울기 계산 - w/o Autograd
$$\begin{aligned}
f^{\prime}(\beta) & =\frac{d}{d \beta}\left(\frac{1}{n} \sum_{i=1}^n\left(x_i-\beta\right)^2\right) \\
& =\frac{1}{n} \sum_{i=1}^n \frac{d}{d \beta}\left(x_i-\beta\right)^2 \\
& =-\frac{1}{n} \sum_{i=1}^n 2\left(x_i-\beta\right)
\end{aligned}$$

```python
answer = - torch.mean(2 * (data - ))
```