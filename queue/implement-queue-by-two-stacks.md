As the title described, you should only use two stacks to implement a queue's actions.

The queue should support`push(element)`,`pop()`and`top()`where pop is pop the first\(a.k.a front\) element in the queue.

Both pop and top methods should return the value of first element.

**Example**

```
push(1)
pop()     // return 1
push(2)
push(3)
top()     // return 2
pop()     // return 2
```

```java
public class MyQueue {
    Stack<Integer> front;
    Stack<Integer> back;
    public MyQueue() {
        front = new Stack<Integer>();
    }

    /*
     * @param element: An integer
     * @return: nothing
     */
    public void push(int element) {
        if (front.empty()) {
            front.push(element);
        } else {
            
            back = new Stack<Integer>();
            while(!front.empty()) {
                back.push(front.pop());
            }
            front.push(element);
            while(!back.empty()) {
                front.push(back.pop());
            }
        }
    }

    /*
     * @return: An integer
     */
    public int pop() {
        if (front.empty()) return -1;
        
        return front.pop();
    }

    /*
     * @return: An integer
     */
    public int top() {
        if (front.isEmpty()) return -1;
        
        return front.peek();
    }
}
```



