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

#### Find One Missing Number

given an array from 1 - N where one number is missing. e.g. **\[1, 2, 4, 5\] N **is** 5 **and missing number is **3**

```js
function findMissingNumber(arr) {
    const N = arr.length;
    const expectedSum = (N + 1) * ((N + 2) / 2);
    let actualSum = 0;
    for (let i = 0; i < N; i++) {
        actualSum += arr[i];
    }

    return expectedSum - actualSum;
}
```

```js
function findMissingNumber(arr) {
    const N = arr.length;
    let totalXOR = 0;
    let arrXOR = 0;
    for (let i = 1; i <= N + 1; i++) {
        totalXOR ^= i;
    } 

    for (let i = 0; i < N; i++) {
        arrXOR ^= arr[i];
    }

    return totalXOR ^ arrXOR;
}
```

#### Find Two Missing Numbers

given an array from 1 - N where two numbers are missing. e.g. **\[1, 2, 5\] **and** N **is** 5 **and missing numbers are \[**3, 4\]**



