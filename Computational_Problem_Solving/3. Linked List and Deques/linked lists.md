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
		self.prev = None
		
	def appendToTail(self, d):
		end = Node(d)
		n = self
		while n.next is not None:
			n = n.next  # point to next node
		n.next = end
```

```python
class LinkedList:
	def __init__(self):
		self.head = None
		
	def append(self, data):
		"""
		appends a new node containing the given data to the end of the linked list
		
		Args:
			data: The data to be stored in the new node.
		"""
		
		new_node = Node(data)
		if self.head is None:
			self.head = new_node
			return
			
		last = self.head
		while last.next:
			last = last.next  # until the end
		last.next = new_node
		
		new_node.prev = last
	
	def print_list(self):
		"""
		prints the contents of the linked list in a space-separated format
		"""
		temp = self.head
		while temp:
			print(temp.data, end=" ")
			temp = temp.next
		print()
```

### Deleting a Node from a Linked List

- Given a node **n**, find the previous node **prev** and set **prev.next** equal to **n.next**.
- Check for the **null pointer** (or None)
- Update the **head** or **tail** pointer as necessary.

```python
def deleteNode(head, d):
	n = head  # initialize a temporary variable n to the head node
	if n.data == d:  # check if the next node's value matches the target value
		return head.next  # if so, returns the next node as the new head, effectively removing the first node.
	while n.next is not None: # iterates through the list until the end is reached
		if n.next.data == d:  
			n.next = n.next.next  # jump twice
			return head  # head didn't change
		n = n.next
	return head
```

- the traverse direction is opposite.

```python
def deleteNodedouble(head, d):
	n = head 
	if n.data == d:
		return head.next
	while n.next is not None:
		if n.next.data ==d:
			n.next = n.next.prev # if so, it skips over the node by linking the current node's next pointer to the node before the one being deleted
			return head
		n = n.prev  # moves to the previous node to continue the traversal
	return head
```