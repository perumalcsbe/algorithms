#### Find Two Missing Numbers

given an array from 1 - N where two numbers are missing. e.g. **\[1, 2, 5\] **and** N **is** 5 **and missing numbers are \[**3, 4\]**

Approach 1: using boolean array visits

```js
function findMissingNumbers(arr) {
  const N = arr.length;
  let boolArr = Array(N + 2).fill(false); //[0, ... N] Natural numbers
  let result = [];
  for (let i = 0; i < N; i++) {
    boolArr[arr[i]] = true;
  }
  for (let i = 1; i < boolArr.length; i++) {
    if (!boolArr[i]) {
      result.push(i);
    }
  }
  return result;
}
```

```
Time Complexity: O(n)
Space Complexity: O(n)
```

Approach 2: using sum & XOR

```js
function findMissingNumbers(arr) {
  const N = arr.length; 
  let totalSum = (N + 2) * ((N + 3) / 2); 
  let arrSum = arr.reduce((s, n) => s + n, 0); 
  let avg = Math.floor((totalSum - arrSum) / 2);
  let totalAvgSum = avg * ((avg + 1) / 2);
  let arrLeftSum = 0;
  let arrRightSum = 0;
  for(let i = 0; i < N; i++) {
    if (arr[i] <= avg) {
      arrLeftSum += arr[i];
    } else {
      arrRightSum += arr[i];
    }
  }
  return [totalAvgSum - arrLeftSum, totalSum - totalAvgSum - arrRightSum];
}
```

```
Time Complexity: O(n)
Space Complexity: O(1)
```



