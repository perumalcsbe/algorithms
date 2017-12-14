Given an array of strings, return all groups of strings that are anagrams.

##### Notice

All inputs will be in **lower-case**

**Example**

Given`["lint", "intl", "inlt", "code"]`, return`["lint", "inlt", "intl"]`.

Given`["ab", "ba", "cd", "dc", "e"]`, return`["ab", "ba", "cd", "dc"]`.

**Approach: Two loops**

```java
public class Solution {
    /*
     * @param strs: A list of strings
     * @return: A list of strings
     */
    public List<String> anagrams(String[] strs) {
        List<String> result = new ArrayList<>();
        if (strs == null || strs.length < 2) {
            return result;
        }
        int n = strs.length;
        boolean[] memo = new boolean[n];
        for (int i = 0; i < n; i++) {
            if (!memo[i]) {
                HashMap<Character, Integer> mapA = new HashMap<>();
                addToHash(mapA, strs[i]);
                
                for (int j = i+1; j < n; j++) {
                    
                    if (!memo[j]) {
                        HashMap<Character, Integer> mapB = new HashMap<>();
                        addToHash(mapB, strs[j]);
                                
                        if (mapA.equals(mapB)) {
                            memo[i] = true;
                            memo[j] = true;
                        }
                    }
                }
            }
        }
        
        for(int x = 0; x < n; x++) {
            if (memo[x]) {
                result.add(strs[x]);
            }
        }
        
        return result;
    }
    
    private void addToHash(Map<Character, Integer> map, String w) {
        for (char c : w.toCharArray()) {
            int count = map.getOrDefault(c, 0);
            map.put(c, ++count);
        }
    }
}
```



