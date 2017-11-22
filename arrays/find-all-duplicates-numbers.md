#### Find All Duplicate Numbers

given an unsorted array **\[1, 7, 2, 6, 5, 6, 5\]**,  duplicates are **\[6, 5\]**

```js
function findDuplicates(arr) {
  let result = [];
  let map = new Map();
  for(let i = 0; i < arr.length; i++) {
    let count = map.get(arr[i]) || 0;

    map.set(arr[i], ++count);
  }

  for(let [key, count] of map.entries()) {
    if (count > 1) {
      result.push(key);
    }
  }

  return result;
}
```



