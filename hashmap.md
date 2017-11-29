

#### JAVA

 Complexity: O \(1\)

```
// Declaration
Map<Integer, Integer> map = new HashMap<>();
Map<Integer, String> map = new HashMap<>();

// Adding entry
//map.put(key, value);
map.put(1, 2);
map.put(2, 3);

// get size
map.size(); // => 2

// get value
//map.get(key);
map.get(1); // => 2
map.get(6); // => null

// check whether HashMap contains a key
//map.containsKey(key);
map.containsKey(1); // true
map.containsKey(6); // false

// to get all keys
Set<Integer> keys = map.keySet();

// to get all values
Collection<Integer> values = map.values();

```

JAVASCRIPT



