Determine whether an integer is a palindrome. Do this without extra space.



**Some hints:**

Could negative integers be palindromes? \(ie, -1\)

If you are thinking of converting the integer to string, note the restriction of using extra space.

You could also try reversing an integer. However, if you have solved the problem "Reverse Integer", you know that the reversed integer might overflow. How would you handle such case?

There is a more generic way of solving this problem.



```js
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(x) {
    // base case 
    if ( x > -1 && x < 10) return true;
    let reverse = 0;
    let y = x; // take copy
    while(x > 0) {
        reverse = (reverse * 10) + (x % 10); 
        x = parseInt(x / 10);
    }
    return reverse === y;
};
```



