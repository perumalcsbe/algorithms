Implement regular expression matching with support for`'.'`and`'*'`.

```
'.' Matches any single character.
'*' Matches zero or more of the preceding element.

The matching should cover the 
entire
 input string (not partial).

The function prototype should be:
bool isMatch(const char *s, const char *p)

Some examples:
isMatch("aa","a") → false
isMatch("aa","aa") → true
isMatch("aaa","aa") → false
isMatch("aa", "a*") → true
isMatch("aa", ".*") → true
isMatch("ab", ".*") → true
isMatch("aab", "c*a*b") → true
```

Approach: Recursion

```js
/**
 * @param {string} s
 * @param {string} p
 * @return {boolean}
 */
const isMatch = (s, p) => {

    if (s == null || p == null) {
        return false;
    }

    let memo = {};

    const matchCore = (i, j) => {
        if (s[i] == undefined && p[j] == undefined) {
            return true;
        }

        if (s[i] != undefined && p[j] == undefined) {
            return false;
        }

        let key = i+'_'+j;

        if (memo[key]) {
            return memo[key];
        }

        if (p[j+1] === '*') {
            if (s[i] === p[j] || (s[i] != undefined && p[j] === '.')) {
                memo[key] = matchCore(i+1, j+2) || matchCore(i+1, j) || matchCore(i, j+2);
                return memo[key];
            } else {
                memo[key] = matchCore(i, j+2);
                return memo[key];
            }    
        }

        if (s[i] === p[j] || (s[i] && p[j] === '.')) {
            memo[key] = matchCore(i+1, j+1);
            return memo[key];
        }

        memo[key] = false;
        return memo[key];
    };

    return matchCore(0, 0);
};
```



