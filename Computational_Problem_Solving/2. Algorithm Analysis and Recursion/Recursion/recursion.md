* Breaks down a problem into **smaller subproblems** to obtain a solution
* A Recursive function consists of two parts
	1. **Base case**: what sholud the algorithm do in the simplest situation?
		- **A condition** that terminates the recursion and prevents an infinite loop. Without base case, recursion never stop! 
		- There must be at **least one case** where it does not fall into any recursion.
		- **Terminating scenario**: does not use recursion to produce an answer
		- **Recursive case**: When repeat recursion, it must converges into base case. 
	2. **Inductive step**: how does the algorithm build up the solution?

**Time complexity of recursive solutions**
- **Time complexity $O(T)$ of a recursive algorithm**: $O(T)=R \times O(s)$ 
	- $R$: The number of recursion invocations
	- $O(S)$: The time complexity of calculation that incurs along with each recursion call
- **Example**: reverse a string
	- `reverse(s) = reverse(s[1...n]) + s[0]`
	- Time Complexity: $O(\text{reverse})=n\times O(1)=O(n)$

**Space complexity of recursive functions**
- Two parts of the space consumption
	- **Recursion-related space + Non-recursion-related space**
- **Recursion-related**
	- **[Stack](https://roi-data.com/entry/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-4-%EC%8A%A4%ED%83%9DStack%EC%9D%B4%EB%9E%80-%EC%97%B0%EC%82%B0-%EA%B5%AC%ED%98%84%EB%B0%A9%EB%B2%95)** to keep track of **recursive function calls**
- **Non-recursion-related**
	- Space that is allocated for the global variables

**Examples**
* Factorials
```python
def factorial(n: int) -> int:

	if n == 0:
		return 1
	else:
		return n * factorial(n - 1)
```

- (HARD PROBLEM) permutation
```python
"""
Problem:
- design an algorithm to print all permutations of a string.
- For simplicity, assume all characters are unique.

input: "abc"
output: ["cab", "acb", "abc", "cba", "bca", "bac"]
"""

def permute(s: str) -> List[str]:
	# base case
	if len(s) == 1:
		return s

	output = []
	for i in range(len(s)):
		# slice the string
		rest = s[:i] + s[i+1:]
		for p in permute(rest):    # here is tricky part
			output.append(s[i] + p)

	return output
```

- Hint: Solve the problem for a **base case** (n = 1) and then try to **build up from there** to get the recurrence (n: the length of a string)
- **Base case and building algorithms from there** often lead to recursive algorithms
--------
***references***
- [recursion](https://iamsjy17.github.io/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98_%EA%B8%B0%EC%B4%88/2019/05/13/recursion1.html)