![[linked lists.png]]

* connected data dispersed throughout memory are **nodes**
* Each node represents one item in the list
* Pointer to the next node's memory address (link) - each node knows **data** and **link**
* First node is referred to as its **head**, and its final node as its **tail**. The last elemet (tail) points to NULL. 

### Basic Operations
1. **Traversing** the linked list
2. **Searching** for an item in the linked list
3. **Inserting** a node to the linked list
4. **Deleting** a node from the linked list

### Creating Linked List

```python
class Node:
	def __init__(self, d):
		self.data = d
		self.next = None # pointer
	def appendToTail(self, d):
		end = Node(d)
		n = self
		while n.next is not None:
			n =
```