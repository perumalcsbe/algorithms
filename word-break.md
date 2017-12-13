Given a string s and a dictionary of words dict, determine if s can be break into a space-separated sequence of one or more dictionary words.

**Example**

Given s =`"lintcode"`, dict =`["lint", "code"]`.

Return true because **"lintcode" **can be break as`"lint code"`.

**Approach: BackTracking**

```
1. For substring W[i:n], recursively find whether substring is in dict
     E[i:j] = [ true if substring matches with dict
              [ false if substring not found in dict then backtrack
              [ neither cases increment i
2. base case: n = 0



"lintcode"
index  string     
i = 0  "l"    => check dict.contains(l) ? l + " " : i++; 
i = 1  "li"   => check dict.contains(li) ? li + " " : i++; 
i = 2  "lin"  => check dict.contains(lin) ? lin + " " : i++; 
i = 3  "lint" => check dict.contains(lint) ? lint + " " : i++; | store answer
i = 4  "c"    => check dict.contains(c) ? c + " " : i++; 
i = 5  "co"   => check dict.contains(co) ? co + " " : i++; 
i = 6  "cod"  => check dict.contains(cod) ? cod + " " : i++;
i = 7  "code" => check dict.contains(code) ? code + " " : i++; | store answer
i = 8  X
```

```java
public class Solution {
    /*
     * @param s: A string
     * @param dict: A dictionary of words dict
     * @return: A boolean
     */
    public boolean wordBreak(String s, Set<String> dict) {
        return find(s, dict);
    }

    private boolean find(String s, Set<String> dict) {

        // base case
        if (s.length() == 0) {
            return true;
        }

        int i = 0;
        String w = "";
        while (i < s.length()) {
            w += s.charAt(i);

            if (dict.contains(w)) {

                if (find(s.substring(i+1), dict)) {
                    return true;
                }

                i++;

            } else {
                i++;
            }
        }

        // if no cases worked then
        return false;

    }
}
```

**Approach: Memorization \(Dynamic Programming\)**

```
From above algorithm, its clear that, there are overlapping subproblems
for e.g.
         (      lintcode                                          )
         /             \       \       \        \      \      \   \
       (intcode)    (ntcode)   (tcode)  (code)   (ode)  (de)  (e)  ("")
      /   \    \              \         \
(ntcode)(tcode)(code)
   /                       
  (tcode)                  
 /                 
(code)

  HashSet memo
    [intcode]  = false
    [ntcode] = false
    [tcode] = false
    [code]  = calculate
    [ode] = false
    [de]= false
    [e] = false

This will not work for larger text                                                                
```

```java
public class Solution {
    /*
     * @param s: A string
     * @param dict: A dictionary of words dict
     * @return: A boolean
     */
    public boolean wordBreak(String s, Set<String> dict) {
        Set<String> memo = new HashSet<>();
        return find(s, dict, memo);
    }

    private boolean find(String s, Set<String> dict, Set<String> memo) {

        // base case
        if (s.length() == 0) {
            return true;
        } else if (memo.contains(s)) {
            return false;
        } else {
            int i = 0;
            String w = "";
            while (i < s.length()) {
                w += s.charAt(i);
                if (dict.contains(w)) {

                    if (find(s.substring(i+1), dict, memo)) {
                        return true;
                    } else {
                        i++;
                    }

                } else {
                    i++;
                }
            }

            memo.add(s);

            // if no cases worked then
            return false;
        }
    }
}
```

**Approach: Tabulation \(Dynamic Programming\)**

```
public class Solution {
    /*
     * @param s: A string
     * @param dict: A dictionary of words dict
     * @return: A boolean
     */
    public boolean wordBreak(String s, Set<String> dict) {
        
        // base case
        if (s == null || s.length() == 0) {
            return true;
        } 
        
        int n = s.length();
        boolean[] dp = new boolean[n+1]; // by default all values are initialized with false
        dp[0] = true;
        
        /**
         * l      i      n      t     c      o      d      e
         * [0,    1,     2,     3,    4,     5,     6,     7      8]
         * [true, false, false, false, true, false, false, false, true]
         */
        
        for (int i = 0; i < n; i++) {
            // if current substring is true
            if (dp[i]) {
                
                for (int j = i+1; j <= n; j++) {
                    String w = s.substring(i, j);
                    if (dict.contains(w)) {
                        dp[j] = true;
                    }
                }
                
            }
        }
        
        
        return dp[n];
        
    }
}
```



