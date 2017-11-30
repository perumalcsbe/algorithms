Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

* push\(x\) -- Push element x onto stack.
* pop\(\) -- Removes the element on top of the stack.
* top\(\) -- Get the top element.
* getMin\(\) -- Retrieve the minimum element in the stack.

**Example:**

```
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> Returns -3.
minStack.pop();
minStack.top();      --> Returns 0.
minStack.getMin();   --> Returns -2.
```

```java
public class MinStack {
    Stack<Integer> stack;
    Stack<Integer> min;
    public MinStack() {
        stack = new Stack<>();
        min = new Stack<>();
    }

    /*
     * @param number: An integer
     * @return: nothing
     */
    public void push(int number) {
        stack.push(number);

        if (min.isEmpty()) {
            min.push(number);
        } else if (min.peek() >= number) {
            min.push(number);
        }
    }

    /*
     * @return: An integer
     */
    public int pop() {
       int top = stack.pop();
       if (!min.isEmpty() && min.peek() == top) {
            min.pop();
        }
       return top;
    }

    /*
     * @return: An integer
     */
    public int min() {
        if (!min.isEmpty()) {
            return min.peek();
        }

        return -1;
    }
}
```

```js
/**
 * initialize your data structure here.
 */
var MinStack = function() {
    this.data = [];
};

/** 
 * @param {number} x
 * @return {void}
 */
MinStack.prototype.push = function(x) {
    this.data.push(x);
};

/**
 * @return {void}
 */
MinStack.prototype.pop = function() {
  this.data.pop();
};

/**
 * @return {number}
 */
MinStack.prototype.top = function() {
    return this.data[this.data.length - 1];
};

/**
 * @return {number}
 */
MinStack.prototype.getMin = function() {
    return Math.min.apply(null, this.data);
};

/** 
 * Your MinStack object will be instantiated and called as such:
 * var obj = Object.create(MinStack).createNew()
 * obj.push(x)
 * obj.pop()
 * var param_3 = obj.top()
 * var param_4 = obj.getMin()
 */
```



