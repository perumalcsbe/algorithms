Given a string S and a string T, find the minimum window in S which will contain all the characters in T in complexity O\(n\).

For example,  
**S**=`"ADOBECODEBANC"`  
**T**=`"ABC"`

Minimum window is`"BANC"`.

**Note:**  
If there is no such window in S that covers all characters in T, return the empty string`""`.

If there are multiple such windows, you are guaranteed that there will always be only one unique minimum window in S.

**Approach: Sliding window**

```
1. Store T target character with its frequency in HashMap. e.g. ABC => {A:1,B:1,C:1}
2. initialize counter with Map size, start, end, head pointer to 0 
3. set len = Integer.MAx_VALUE - problem needs minimum window
4. Traverse S with end pointer till end of string S 
        reduce Map character frequency { if there is match 
        reduce counter
       if counter becomes 0 then target chars found. now find length
         look for first match in MAP
         increment counter by 1, update head with first match pos start
         calculate len by end-start      
5. finally return len         
```

```java
class Solution {
    public String minWindow(String s, String t) {
        // base case
        if (t.length() > s.length()) {
            return "";
        }
        
        // store T characters with its frequences in HashMap
        Map<Character, Integer> map = new HashMap<>();
        // traverse target string and update it map
        for (char c: t.toCharArray()) {
            map.put(c, map.getOrDefault(c, 0) + 1);
        }
        
        int counter = map.size(); // target characters count
        int start = 0; // to hold start pos of first matched target char
        int end = 0; // to hold end of last matched target char
        int head = 0; // to hold min length start pos
        int len = Integer.MAX_VALUE; // to hold min length result
        
        while (end < s.length()) {
            char c = s.charAt(end);
            if (map.containsKey(c)) {
                map.put(c, map.get(c)-1);
                if (map.get(c) == 0) {
                    counter--;
                }
            }
            end++;
            
            // find first pos of match
            while (counter == 0) {
                char d = s.charAt(start);
                
                if (map.containsKey(d)) {
                    map.put(d, map.get(d)+1);
                    if (map.get(d) > 0) {
                        counter++;
                    }
                }
                
                if (end-start < len) {
                    len = end - start;
                    head = start;
                }
                
                start++;
            }
        }
        
        
        if (len == Integer.MAX_VALUE) {
            return "";
        }
        
        return s.substring(head, head+len);
        
    }
}
```



