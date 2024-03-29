### Space Complexity

The amount of space or memory taken by the algorithm to run as a function of its input length
- Include auxiliary space and space used by the input.
- Auxiliary space: the temporary or extra space the algorithm consumes

**Problem**: If there are N data elements, how many units of memory will the algorithm consume?
- **Simple Array Storage**: If simple array, the memory usage will be directly proportional to the number of elements (N). So its **O(N)**
- **Data Structures with Fixed Overhead**: If the algorithm uses the data structures with a fixed overhead per element (e.g., a linked list node with a pointer and data field), the memory usage will grow linearly with the number of elements (N) but with a constant additional term. So this can be expressed as **O(N) + c**, where c is a constant representing the fixed overhead