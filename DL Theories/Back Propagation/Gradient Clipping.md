reference = https://sanghyu.tistory.com/87

gradient exploding을 방지하여 학습의 안정화를 도모하기 위해 사용하는 방법이다. gradient가 threshold를 넘어가면 clipping을 해준다. clipping은 gradient의 L2 norm으로 나눠주는 방식으로 진행된다. threshold의 경우 gradient가 가질 수 있는 최대 L2 norm을 뜻하고 이는 hyperparameter로 사용자가 설정해주어야 한다.

$$\begin{aligned}
\frac{\partial \epsilon}{\partial \theta} \leftarrow & \begin{cases}\frac{\text { threshold }}{\|\hat{g}\|} \hat{g} & \text { if }\|\hat{g}\| \geq \text { threshold } \\
\hat{g} & \text { otherwise }\end{cases} \\
& \text { where } \hat{g}=\frac{\partial \epsilon}{\partial \theta} .
\end{aligned}$$

Gradient clipping이 없으면 gradient exploding이 발생하여 global minimum에 도달하지 못하고 엉뚱한 방향으로 향하게 되지만, clipping을 하게 되면 gradient vector가 방향은 유지하되 적은 값만큼 이동하여 도달하려고 하는 곳에 안정적으로 내려가게 된다. 

**Example**
```python
import torch

max_norm = 5
optimizer = torch.optim.Adam(model.parameters(), lr=1e-3, weight_decay=0)

optimizer.zero_grad()
loss.backward()
torch.nn.utils.clip_grad_norm_(model.parameters(), max_norm)
optimizer.step()
```
