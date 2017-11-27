**Input:– 4 -&gt; 8 -&gt; 15 -&gt; 16 -&gt; 23 -&gt; 42**

**Output:– 42 -&gt; 23 -&gt; 16 -&gt; 15 -&gt; 8 -&gt; 4**



```js
function reverseList(head) {
    let temp = null;
    let nextNode = null;
    
    while(head) {
        nextNode = head.next;
        head.next = temp;
        temp = head;
        head = nextNode;
    }
    
    return temp;
}
```



