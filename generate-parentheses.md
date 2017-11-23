Givennpairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, givenn= 3, a solution set is:

```
[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
```

```js
/**
 * @param {number} n
 * @return {string[]}
 */
var generateParenthesis = function(n) {
    let result = [];
    const dfs = function(str, left, right) {

        if (left > right) return;

        if (left === 0 && right === 0) {
            result.push(str);
            return;
        }

        if ( left > 0) dfs(str + '(', left - 1, right);
        if ( right > 0) dfs(str + ')', left, right - 1);

    };



    dfs('', n, n);

    return result;
    
};
```



