* Breaks down a problem into **smaller subproblems** to obtain a solution
* A Recursive function consists of two parts
	1. **Base case**: what sholud the algorithm do in the simplest situation? → 적어도 하나의 recursion에 빠지지 않는 경우가 존재해야 한다. 
		- **Terminating scenario**: does not use recursion to produce an answer
		- Without base cases, an algorithm would never terminate!
		- **Recursive case**: recursion을 반복하다보면 결국 base case로 수렴해야 한다. 
	2. **Inductive step**: how does the algorithm build up the solution?

**Time complexity of recursive solutions**
- **Time complexity $O(T)$ of a recursive algorithm**: $O(T)=R \times O(s)$ 