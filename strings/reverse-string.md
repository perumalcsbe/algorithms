### Reverse String

Write a function that takes a string as input and returns the string reversed.

**Example:**  
Given s = "hello", return "olleh".

##### Approach 1:  reverse loop

```js
/**
 * @param {string} s
 * @return {string}
 */
function reverseString(s) {
    let result = '';

    for (let i = s.length - 1; i >= 0; i--) {
        result += s[i];
    }

    return result;
}
```

```
Time Complexity: O(n)
Space Complexity: O(1)
```

##### Approach 2: Built-in methods

```js
/**
 * @param {string} s
 * @return {string}
 */
function reverseString(s) {
    return s.split('').reverse().join('');
}
```

##### Approach 3: [Two Pointers](/two-pointers.md) {#two-pointers}

_Note: Javascript String is immutable. so swapping indices can be done differently_

```js
function swap(s, start, end) {
    return s.substring(0, start) + s[end] + s.substring(start + 1, end) + s[start] + s.substring(end + 1);
}

**
 * @param {string} s
 * @return {string}
 */
function reverseString(s) {
   let i = 0;
   let j = s.length - 1;
   while( i < j ) {
     swap(s, i, j);
     i++;
     j--
   }

   return s; 
}
```



