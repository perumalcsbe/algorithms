### Dequeue

```java
// declaration
Deque deque = new LinkedList<>();

// add: Adds an element to the tail.
dequeue.add("item1");
dequeue.add("item2");
// output: item1->item2

// addFirst: Adds an element to the head.
dequeue.addFirst("item1");
dequeue.addFirst("item2");
// output: item2 -> item1

// addLast: Adds an element to the tail.
dequeue.addFirst("item1");
dequeue.addFirst("item2");
// output: item1 -> item2
```

```
Methods of deque:

add(element): Adds an element to the tail.
addFirst(element): Adds an element to the head.
addLast(element): Adds an element to the tail.
offer(element): Adds an element to the tail and returns a boolean to explain if the insertion was successful.
offerFirst(element): Adds an element to the head and returns a boolean to explain if the insertion was successful.
offerLast(element): Adds an element to the tail and returns a boolean to explain if the insertion was successful.
iterator(): Returna an iterator for this deque.
descendingIterator(): Returns an iterator that has the reverse order for this deque.
push(element): Adds an element to the head.
pop(element): Removes an element from the head and returns it.
removeFirst(): Removes the element at the head.
removeLast(): Removes the element at the tail.
```



