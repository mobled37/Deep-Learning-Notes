### Space Complexity

The amount of space or memory taken by the algorithm to run as a function of its input length
- Include auxiliary space and space used by the input.
- Auxiliary space: the temporary or extra space the algorithm consumes
- **In this note, space complexity and auxiliary space will be interchangeably used**

**Problem**: If there are N data elements, how many units of memory will the algorithm consume?
- **Simple Array Storage**: If simple array, the memory usage will be directly proportional to the number of elements (N). So its **O(N)**
- **Data Structures with Fixed Overhead**: If the algorithm uses the data structures with a fixed overhead per element (e.g., a linked list node with a pointer and data field), the memory usage will grow linearly with the number of elements (N) but with a constant additional term. So this can be expressed as **O(N) + c**, *where c is a constant representing the fixed overhead*.
- **Nested Data Structures**: If the algorithm uses nested data structures (e.g., a dictionary of arrays), the memory useage might grow proportionally to a higher power of N depending on the nesting depth. So its **O(N)**

### Time Complexity

The amount of time taken by an algorithm to complete its process as a function of its input length.
- The number of primitive operations or steps executed in the algorithm.
- **In this note, time complexity, speed, efficiency, runtime, running time will be interchangeably used**


