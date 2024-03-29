### Big-Oh

- Given a function $g(n)$, $O(g(n))=\{ f(n): \text{there exist positive constants } c \text{ and } n_0 \text{ such that } 0 \le f(n) \le cg(n) \text{ for all } n \geq n_0 \}$   
- An algorithm takes $O(g(n))$ if its running time is upper-bounded by $cg(n)$.
	- $O(n), O(nlogn), O(n^2), O(2^n)$

![[big-oh notation.png]]
- Intuitively, $f(n) \in O(g(n))$ → $f$ grows no faster than $g$.

### Big-Theta

- Given a function $g(n), \Theta(g(n))=\left\{f(n) \text { : there exist positive constants } c_1, c_2, n_0 \text { s.t. } c_1 g(n) \leq f(n) \leq c_2 g(n) \text { for all } n \geq n_0\right\}$
- An algorithm takes $\Theta(g(n))$ if its running time is **lower-bounded by** $c_1g(n)$ and **upper-bounded by** $c_2g(n)$.
- More precise than the big-oh notation

![[big-theta notation.png]]
- **M**