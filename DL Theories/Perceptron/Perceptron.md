***
**2.1. Perceptron**

다수의 신호를 입력으로 받아 하나의 신호 출력

input = $x_1, x_2$
output = $y$
weight = $w_1, w_2$ ≈ resistance, opposite direction

input and output called **neuron** or **node**  

뉴런에서 보내온 신호의 총합이 정해진 한계를 넘어설 때만 1을 출력, (뉴런이 활성화한다) - $\theta$, **threshold**

$$y=\left\{\begin{array}{l}0\left(w_1 x_1+w_2 x_2 \leq \theta\right) \\ 1\left(w_1 x_1+w_2 x_2>\theta\right)\end{array}\right.$$
***
**2.2.1 AND Gate**

두 입력이 모두 1일 때만 1을 출력, 그 외에는 0을 출력

|$x_1$|$x_2$|$y$|
|---|---|---|
|0|0|0|
|1|0|0|
|0|1|0|
|1|1|1|

**Example**
$(w_1, w_2, \theta)$ = (0.5, 0.5, 0.7) / (0.5, 0.5, 0.9) / (1.0, 0.1, 1.0) - OK

***
**2.2.2 NAND and OR Gate**

**NAND**
= Not AND

$x_1$ && $x_2$ == 1 일 때만 0 출력, 그 외에는 1 출력

|$x_1$|$x_2$|$y$|
|---|---|---|
|0|0|1|
|1|0|1|
|0|1|1|
|1|1|0|

**OR**
$x_1$ or $x_2$ == 1 일때 1 출력, 그 외에는 0

|$x_1$|$x_2$|$y$|
|---|---|---|
|0|0|0|
|1|0|1|
|0|1|1|
|1|1|1|