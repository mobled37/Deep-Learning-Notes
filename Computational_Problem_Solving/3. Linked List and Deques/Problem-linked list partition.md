
Problem
- Write a code to partition a linked list around a value x, such that all nodes less than x come before all nodes greater than or equal to x. If x is contained within the list, the values of x only need to be after the elements less than x. The partition elemment x can appear anywhere in the "right partition", it does not need to appear between the left and right partitions.

Example
- input: head of linked list 3 -> 5 -> 8 -> 5 -> 10 -> 2 -> 1, x = 5
- output: 3 -> 1 -> 2 -> 10 -> 5 -> 5 -> 8

Hint
- There is a point in the linked list before which all the elements are smaller than x and after which all the elements would be greater or equal to x. Lets call this point as the Joint.
- We aim to create these two linked lists and join them

```python
def partition(head: Node, x: int) -> Node: # head is linkedlist
	curr = head
	left, right = None, None # both left and right are nodes
	left_head = None
	mid = None
	
	while curr: # iterate over when curr is None
		if curr.data < x:
			if left: # if left is not None
				left.next = curr
				left = left.next
			else: # left is None
				left_head = left = curr
		else: # curr.data >= x
			if right: # if right is not None
				right.next = curr
				right = right.next
			else: # if right is None
				right = curr
				mid = curr
		curr = curr.next
		
	# connect two seperate list
	if left:
		left.next = mid
		head = left_head
	else:
		head = mid
		
	if right: # right is not None
		right.next = None # end of linkedlist
		
	return head

  
  

if __name__ == "__main__":

	head = Node(3)
	r = [5, 8, 5, 10, 2, 1]
	
	for elem in r:
		head.appendToTail(elem)
	
	out = partition(head, 5)
	output_list = []
	
	while out:
		output_list.append(out.data)
		out = out.next
		
	print(output_list) # [3, 2, 1, 5, 8, 5, 10]
```

