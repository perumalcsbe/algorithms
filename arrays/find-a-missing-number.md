#### Find A Missing Number

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



