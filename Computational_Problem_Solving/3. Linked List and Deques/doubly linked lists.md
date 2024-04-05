
![[doubly linked lists.png]]

- **Doubly linked list**: each node has two links - next and prev.
- Doubly linked list always keeps track of both the first and last nodes. 

**Advantage**
- **navigate** in both direction
- **delete** a node even if we don't have the previous node's address

**Disadvantages**
- due to extra pointer, requiring more space.
- Insertion or deletion of a node takes a bit longer (more pointer operations).