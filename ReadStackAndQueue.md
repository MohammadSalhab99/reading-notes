Data structure organizes the storage in computers so that we can easily access and change data. Stacks and Queues are the earliest data structure defined in computer science. A simple Python list can act as a queue and stack as well. A queue follows FIFO rule (First In First Out) and used in programming for sorting. It is common for stacks and queues to be implemented with an array or linked list.

## Stack
A Stack is a data structure that follows the LIFO(Last In First Out) principle. To implement a stack, we need two simple operations:

push - It adds an element to the top of the stack.
pop - It removes an element from the top of the stack.

### Operations:

Adding - It adds the items in the stack and increases the stack size. The addition takes place at the top of the stack.
Deletion - It consists of two conditions, first, if no element is present in the stack, then underflow occurs in the stack, and second, if a stack contains some elements, then the topmost element gets removed. It reduces the stack size.
Traversing - It involves visiting each element of the stack.
![python-stack-and-queue](https://user-images.githubusercontent.com/61474974/160258733-d3db9503-3945-4b4e-ad7a-65dfeadcf06c.png)

### Characteristics:



Insertion order of the stack is preserved.
Useful for parsing the operations.
Duplicacy is allowed.

## Queue
A Queue follows the First-in-First-Out (FIFO) principle. It is opened from both the ends hence we can easily add elements to the back and can remove elements from the front.

To implement a queue, we need two simple operations:

enqueue - It adds an element to the end of the queue.
dequeue - It removes the element from the beginning of the queue.
![python-stack-and-queue-2](https://user-images.githubusercontent.com/61474974/160258737-a08b9d9c-1706-4adc-957a-73eacd447bdd.png)

### Operations on Queue

Addition - It adds the element in a queue and takes place at the rear end, i.e., at the back of the queue.
Deletion - It consists of two conditions - If no element is present in the queue, Underflow occurs in the queue, or if a stack contains some elements then element present at the front gets deleted.
Traversing - It involves to visit each element of the queue.

### Characteristics

Insertion order of the queue is preserved.
Duplicacy is allowed.
Useful for parsing CPU task operations.

source : https://www.javatpoint.com/python-stack-and-queue
