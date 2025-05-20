Resizable-array implementation of the [`Deque`](https://docs.oracle.com/javase/8/docs/api/java/util/Deque.html "interface in java.util") interface. Array deques have no capacity restrictions; they grow as necessary to support usage.
This class is likely to be faster than [`Stack`](https://docs.oracle.com/javase/8/docs/api/java/util/Stack.html "class in java.util") when used as a stack, and faster than [`LinkedList`](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html "class in java.util") when used as a queue.

- **Better cache locality** and less pointer overhead compared to linked lists.
- **No synchronization overhead** compared to `Stack` (which is synchronized).
- Efficient **circular array** implementation that resizes dynamically with less overhead.

