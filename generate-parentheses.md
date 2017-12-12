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

```java
public class Solution {
    /*
     * @param n: n pairs
     * @return: All combinations of well-formed parentheses
     */
    public List<String> generateParenthesis(int n) {
        List<String> result = new ArrayList<String>();
        // base case
        if (n < 1) {
            return result;
        }
        
        dfs("", n, n, result);
        
        return result;
    }
    
    private void dfs(String s, int prefix, int suffix, List<String> list) {
        // Base case
        if (prefix > suffix) {
            return;
        }
        
        if (prefix == 0 && suffix == 0) {
            list.add(s);
            return;
        }
        
        if (prefix > 0) {
            dfs(s + "(", prefix-1, suffix, list);
        }
        
        if (suffix > 0) {
            dfs(s + ")", prefix, suffix-1, list);
        }
    }
}
```



