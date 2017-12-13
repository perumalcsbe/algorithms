Remove the minimum number of invalid parentheses in order to make the input string valid. Return all possible results.

Note: The input string may contain letters other than the parentheses`(`and`)`.

**Examples:**

```
"()())()"  - ["()()()", "(())()"]
"(a)())()" - ["(a)()()", "(a())()"]
")("       - [""]
```

```
Approach: greedy
  skip if char is not ( or )
  if char is (
    if next char is not [a-z]
      include ) and check rest of them are valid
      exclude ) and check rest of them are valid
      
 input "()())()"
 result ""
      
  
```

```js
/**
 * @param {string} s
 * @return {string[]}
 */
var removeInvalidParentheses = function(s) {

};
```



