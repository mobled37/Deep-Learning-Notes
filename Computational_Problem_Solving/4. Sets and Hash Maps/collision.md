**Collision**
- Hash functions are used to ==map each key to a different address space==. Practically, this is not possible, and collision occurs. 
- **Collision**: the situation that two keys are ==mapped into the same location in the hash table==.
	- let hash function $h$ be $h(x) = x.length$
	- $h("Tom") = 3$
	- $h("Sam")=3$ 
- The worst-case performance for lookup is $O(n)$.