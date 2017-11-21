# Array

#### Find Pivot Index

```js
function pivotIndex(arr) {
  const sum = arr.reduce((s, n) = s + n, 0);
  let leftSum = 0;
  for(let i = 0; i < arr.length; i++) {
    if (leftSum === (sum - leftSum - arr[i])) return i;

    leftSum += arr[i];
  }

  return -1;
}
```

#### Find All Duplicates

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



