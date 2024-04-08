
* Iterate through the linked list with two pointers simultaneously, with one ahead of the other. 
* "Fast" node might be ahead by a fixed amount

**Algorithm**
1. Initialize two pointers **before** and **after**. (Initialize these two with a dummy node)
2. Iterate the original linked list using the head pointer
3. If the node's value pointed by head is **lesser** than x, the node should be part of the list **before**. Move it to list before
4. Else, the node should be part of list **after**. Move it to list **after**.