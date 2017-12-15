Given k strings, find the longest common prefix \(_LCP_\).

**Example**

For strings`"ABCD"`,`"ABEF"`and`"ACEF"`, the LCP is`"A"`

For strings`"ABCDEFG"`,`"ABCEFG"`and`"ABCEFA"`, the LCP is`"ABC"`

**Approach: Two loops**

```
  [A B] C D
  [A B] E F
  [A] C E F
  
  [A] [B] [C] D E F G
  [A] [B] [C] E F G
  [A] [B] [C] E F A
  
 Algorithm
 1. base cases: 
     a. empty array return empty lcp
     b. array has one string return first string
 2. Take first string and at each character traverse the rest of array strings and find match 
 
 Improvements: find min length of all strings then run loop with min length rather then first string length
```

```java
public class Solution {
    /*
     * @param strs: A list of strings
     * @return: The longest common prefix
     */
    public String longestCommonPrefix(String[] strs) {
       String lcp = "";
       // base case
       if (strs == null || strs.length < 1) {
           return lcp;
       }
       
       // if there is only one string in array then its LCP
       if (strs.length == 1) {
           return strs[0];
       }
       
       // take first string 
       for (int j = 0; j < strs[0].length(); j++) {
           
            char ch = strs[0].charAt(j);
            // traverse rest of strings and check any match found at same index           
            for (int i = 1; i < strs.length; i++) {
                // check length of each string 
                if (j >= strs[i].length()) {
                     return lcp;
                }
                
                // if characters don't match then return LCP so far         
                if (strs[i].charAt(j) != ch) {
                    return lcp;
                }
                
            }
            // if loop is success then its a match
            lcp += ch;
       }
       
       return lcp;
    }
}
```



