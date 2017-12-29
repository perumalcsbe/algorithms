### Rabin-Karp algorithm

```
1. Take hasCode() of pattern
2. compare hashCode() of source
    
```

```java
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public int strStr(final String A, final String B) {
        // base cases
        if (A.length() == 0 && B.length() == 0 || B.length() == 0) {
            return -1;
        }
        
        int m = A.length();
        int n = B.length();
        
        int needleHash = B.hashCode(); // get needle hash code
        
        // this will be short
        for (int i = 0; i < m; i++) {
            if (i+n <= m) {
                
                String sub = A.substring(i, i+n);
                
                int subHash = sub.hashCode();
                
                if (needleHash == subHash) {
                    
                    int k = 0;
                    boolean found = true;
                    
                    
                    for (int j = i; j < i+n; j++) {
                        if (A.charAt(j) == B.charAt(k)) {
                            k++;
                        } else {
                            found = false;
                            break;
                        }
                    }
                    
                    
                    if (found) {
                        return i;
                    }
                    
                }
                
            }
        }
        
        
        return -1;
    }
}

```



