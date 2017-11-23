Given a string containing just the characters`'('`,`')'`,`'{'`,`'}'`,`'['`and`']'`, determine if the input string is valid.

The brackets must close in the correct order,`"()"`and`"()[]{}"`are all valid but`"(]"`and`"([)]"`are not.

```js
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    if (s.length < 2) return false;

    var expected = [];
    var openBraceList = ['(', '{', '['];
    var closeBraceList = [')', '}', ']'];
    for(var i = 0 ; i < s.length; i++) {
        // check if its open brace
        var index = openBraceList.indexOf(s[i]); // [ (
        var cIndex = closeBraceList.indexOf(s[i]); // ) ]
        if (index > -1) {
            expected.push(closeBraceList[index]); //]
        }
        else if (cIndex > -1 && expected.length > 0) {
            if (s[i] !== expected.pop()) { 
                return false;
            }
        } else {
            return false;
        }
    }

    return expected.length === 0;
};
```



