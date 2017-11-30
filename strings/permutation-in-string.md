Given two strings **s1 **and **s2**, write a function to return true if **s2 **contains the permutation of **s1**. In other words, one of the first string's permutations is the **substring **of the second string.

**Example 1:**

```
Input: s1 = "ab" s2 = "eidbaooo"

Output: True

Explanation: s2 contains one permutation of s1 ("ba").
```

**Example 2:**

```
Input: s1= "ab" s2 = "eidboaoo"

Output: False
```

**Note:**

1. The input strings only contain lower case letters.
2. The length of both given strings is in range \[1, 10,000\].

**Approach: Map**

```js
/**
 * @param {string} s1
 * @param {string} s2
 * @return {boolean}
 */
var checkInclusion = function(s1, s2) {
    if (s2.length < s1.length || s2.length === 0 ||  s1.length === 0) return false;
    
    let map = new Map();
    let len = s1.length;
    for (let i = 0; i < len; i++) {
        map.set(s1[i], 1 + (map.get(s1[i]) || 0))
    }
    
    let count = map.size; 
    let start = 0;
    let end = 0;
    
    while(end < s2.length) {
        let ch = s2[end];
        
        if (map.has(ch)) { 
            map.set(ch, map.get(ch) - 1); 
            if(map.get(ch) === 0) {
                count--;
            }
        }
        
        while(count === 0) {
            if (end - start + 1 === len) {
                return true;
            }
            let ch = s2[start]; 
            if (map.has(ch)) {
                map.set(ch, map.get(ch) + 1);
                if(map.get(ch) > 0) {
                    count++;
                } 
            }
            
            start++;
        }
        
        end++;
    }
    
    return false;
};
```



**Approach: Boolean Array**

```js
/**
* @param {string} s1
* @param {string} s2
* @return {boolean}
*/
var checkInclusion = function(s1, s2) {
  // check if s1 is bigger than s2 then return false  
  if (s2.length < s1.length) return false;
  
  // create an array with length of 256 filled with 0s
  let chars = Array(256).fill(0);
  let len = s1.length;
  
  // traverse string s1 and get char code and increament them
  for(let i = 0; i < len; i++) {
      chars[+s1.charCodeAt(i)]++; // increment charCode 
  }

  
  let cnt = len; // s1 count
  // two pointers start & end initialize with 0
  let start = 0;
  let end = 0;
  
  // traverse end pointer reaches end of s2
  while(end < s2.length) {
  
    // if there is a match of s1 char s1[i] === s2[j] then 
    //      decreament count of all s2[end] 
    // then decreament s1 count
    if (chars[s2.charCodeAt(end++)]-- > 0) cnt--;
    
    // if s1 count is 0 then s1 chars are present in s2
    while(cnt === 0) {
  
      // if difference of end and start pointer is equal to s1 length then its found  
      if (end - start === len) return true;
      // matched chars of s1 & s2 are marked to 0
      // if there is a match of s1 char s1[i] === s2[j] then 
      //      decreament count of all s2[end] 
      // then decreament s1 count 
      if (chars[s2.charCodeAt(start++)]++ === 0) cnt++;
    }
  }
  
  return false;
}
```



