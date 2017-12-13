Given two words _word1 \_and \_word2_, find the minimum number of steps required to convert word1 to word2. \(each operation is counted as 1 step.\)

You have the following 3 operations permitted on a word:

* Insert a character
* Delete a character
* Replace a character

**Example**

Given word1 =`"mart"`and word2 =`"karma"`, return`3`.

**Approach: Dynamic Programming**

```
m a r t => k a r m a

k a r m a
m a r t 
- 0 0 - -
```

| m\*n | 0 "" | 1 m | 2 a | 3 r | 4 t |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 0 "" | 0 | 1 | 2 | 3 | 4 |
| 1 k | 1 | 1 | 2 | 3 | 4 |
| 2 a | 2 | 2 | 1 | 2 | 3 |
| 3 r | 3 | 3 | 2 | 1 | 2 |
| 4 m | 4 | 3 | 3 | 2 | 2 |
| 5 a | 5 | 4 | 3 | 3 | 3 |

```java
public class Solution {
    /*
     * @param word1: A string
     * @param word2: A string
     * @return: The minimum number of steps.
     */
    public int minDistance(String word1, String word2) {
       //base case
       
       if (word1.length() == 0 && word2.length() == 0) {
           return 0;
       }
       
       /**
        * m*n   0"" 1m  2a  3r  4t
        * 0""	0	1	2	3	4
        * 1 k	1	1	2	3	4
        * 2 a	2	2	1	2	3
        * 3 r	3	3	2	1	2
        * 4 m	4	3	3	2	2
        * 5 a	5	4	3	3	3
        */
       
       int m = word2.length();
       int n = word1.length();
       int[][] dp = new int[m + 1][n + 1];
       
       
       // fill top row
       for (int col = 0; col < n + 1; col++) {
           dp[0][col] = col;
       }
       
       // fill left col
       for (int row = 0; row < m + 1; row++) {
           dp[row][0] = row;
       }
       
       // for dp[i][j]
       //     take min( dp[i - 1, j]+1, dp[i, j -1]+1, dp[i-1, j -1] + diff(word2[i], word1[j]))
       
       for (int i = 1; i < m + 1; i++) {
           
           for (int j = 1; j < n + 1; j++) {
               int diff = word1.charAt(j-1) == word2.charAt(i-1) ? 0 : 1;
               dp[i][j] = minimum(1+dp[i-1][j], 1+dp[i][j-1], diff+dp[i-1][j-1]);
           }
           
       }
       
       
       return dp[m][n];
    }
    
    private int minimum(int a, int b, int c) {
        if (b < a) {
            a = b;
        }
        
        if (c < a) {
            a = c;
        }
        
        return a;
    }
}
```



