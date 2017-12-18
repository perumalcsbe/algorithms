Alice is taking a cryptography class and finding_anagrams_to be very useful. We consider two strings to be anagrams of each other if the first string's letters can be rearranged to form the second string. In other words, both strings must contain the same exact letters in the same exact frequency For example,`bacdc`and`dcbac`are anagrams, but`bacdc`and`dcbad`are not.

Alice decides on an encryption scheme involving two large strings where encryption is dependent on the minimum number of character deletions required to make the two strings anagrams. Can you help her find this number?

Given two strings,and, that may or may not be of the same length, determine the minimum number of character deletions required to makeandanagrams. Any characters can be deleted from either of the strings.

**Constraints**

* It is guaranteed that and consist of lowercase English alphabetic letters \(i.e.,through\).

**Output Format**

Print a single integer denoting the number of characters you must delete to make the two strings anagrams of each other.

**Sample Input**

```
cde
abc
```

**Sample Output**

```
4
```

**Explanation**

We delete the following characters from our two strings to turn them into anagrams of each other:

1. Remove`d`and`e`from`cde`to get`c`.
2. Remove`a`and`b`from`abc`to get`c`.

We must deletecharacters to make both strings anagrams, so we printon a new line.



```java
class Solution {
    public static int numberNeeded(String first, String second) {
        int[] counter = new int[26];
        int result = 0;
        for (char a: first.toCharArray()) {
            counter[a-'a']++;
        }
        for (char b: second.toCharArray()) {
            counter[b-'a']--;
        }
        
        for (int i = 0; i < counter.length; i++) {
            result += Math.abs(counter[i]);
        }
        
        return result;
    }
}    
```



