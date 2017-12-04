

## Priority Queue

by default the Pri­or­ity Queue works as min-Heap

```java
PriorityQueue<Integer> pq = new PriorityQueue<Integer>();

// insert
pq.offer(value);

// to get last item
pq.peek();

// to extract min value
pq.poll();

// to get size
pq.size();

```

For Max-Heap

```java
PriorityQueue<Integer> pq = new PriorityQueue<Integer>(N, new Comparator<Integer>() {
    public int compare(Integer o1, Integer o2) {
    	return o2 - o1;
    }
});
```



