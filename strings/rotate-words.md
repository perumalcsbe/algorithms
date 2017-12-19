The words are same rotate words if rotate the word to the right by loop, and get another. Count how many different rotate word sets in dictionary.

E.g. picture and turepic are same rotate words.

##### Notice

All words are lowercase.

**Example**

Given dict =`["picture", "turepic", "icturep", "word", "ordw", "lint"]`  
return`3`.

`"picture", "turepic", "icturep"`are same ratote words.  
`"word", "ordw"`are same too.  
`"lint"`is the third word that different from the previous two words.



**Approach: Naive O\(N^2\)**

```java
public class Solution {
    /*
     * @param words: A list of words
     * @return: Return how many different rotate words
     */
    public int countRotateWords(List<String> words) {
        if (words.size() < 2) {
            return words.size();
        }
        
        int i = 0; 
        while(i < words.size()) {
            
            int j = i+1; 
            
            while(j < words.size()) { 
                if (isSubstring(words.get(i), words.get(j))) {
                    words.remove(j);
                } else {
                    j++;
                }
            }
            
            i++;
        }
        
        return words.size();

    }
    
    
    private boolean isSubstring(String a, String b) {
        if (a.length() != b.length()) {
            return false;
        }
        /**
        * if string b is roation String a then
        * b = b+b;
        * a should be subtring of it
        **/
        b = b+b;
        return b.contains(a);
    }
}
```



