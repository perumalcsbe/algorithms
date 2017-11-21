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



