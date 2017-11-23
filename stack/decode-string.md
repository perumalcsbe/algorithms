Given an encoded string, return it's decoded string.

The encoding rule is:`k[encoded_string]`, where theencoded\_stringinside the square brackets is being repeated exactlyktimes. Note thatkis guaranteed to be a positive integer.

You may assume that the input string is always valid; No extra white spaces, square brackets are well-formed, etc.

Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers,k. For example, there won't be input like`3a`or`2[4]`.

**Examples:**

```
s = "3[a]2[bc]", return "aaabcbc".
s = "3[a2[c]]", return "accaccacc".
s = "2[abc]3[cd]ef", return "abcabccdcdcdef".
```

```js
/**
 * @param {string} s
 * @return {string}
 */
var decodeString = function(s) {
    let charStack = []; 
    let intStack = []; 
    let i = 0;
    while(i < s.length) { 
          if (/[0-9]/g.test(s[i])) {
              let n = ''; 
              while(/[0-9]/g.test(s[i])) {
                  n += s[i];
                  i++; 
              }
              intStack.push(+n);
              --i; 
          } else if (s[i] === ']') {
              let str = '';
              while(charStack[charStack.length - 1] !== '[') {
                  str = charStack.pop() + str; 
              }
              
              charStack.pop(); 
              
              charStack.push(str.repeat(intStack.pop())); 
              
          } else {
              charStack.push(s[i]); 
          }
        i++;
    }
    
    return charStack.join('');
};
```



