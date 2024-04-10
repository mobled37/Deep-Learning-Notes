- **hashing**: the process of taking elements and converting them to numbers
- **hash map**: data structure that stores the **keys and values** by mapping keys to their associated values via a has function
	- A list of (**key, value**) pairs (Hash table associates keys with values using a hash function)
	- also known as **hash maps, maps, dictionaries, or associative arrays**

**Collision**
- Hash functions are used to ==map each key to a different address space==. Practically, this is not possible, and collision occurs. 
- **Collision**: the situation that two keys are ==mapped into the same location in the hash table==.
	- let hash function $h$ be $h(x) = x.length$
	- $h("Tom") = 3$
	- $h("Sam")=3$ 
- The worst-case performance for ll