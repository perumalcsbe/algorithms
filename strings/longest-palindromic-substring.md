Given a string **s**, find the longest palindromic substring in **s**. You may assume that the maximum length of **s **is 1000.

**Example:**

```
Input:"babad"
Output:"bab"
Note:"aba" is also a valid answer.
```

**Example:**

```
Input:"cbbd"
Output:"bb"
```

```
b a b a d
[b] √
[b a] x
[b a b] √
[b a b a] x
[b a b a d] x 
  [a] √
  [a b] x
  [a b a] √
  [a b a d] x
    [b] √
    [b a] x
    [b a d] x

 c b b d
[c] √
[c b] x
[c b b] x
[c b b d] x
  [b] √
  [b b] √
  [b b d] x
     [b] √
     [b d] x
       [d] √
```

```java
class Solution {
    public String longestPalindrome(String s) {
        if (s.length() < 2 || isPalindrome(s)) {
            return s;
        }
        String res = Character.toString(s.charAt(0));
        int maxLen = 0;
        for (int i = 0; i < s.length(); i++) {
            StringBuffer temp = new StringBuffer();
            temp.append(s.charAt(i));
            for (int j = i+1; j < s.length(); j++) {
                temp.append(s.charAt(j));
                if (isPalindrome(temp.toString()) && temp.length() > maxLen) {
                    res = temp.toString();
                    maxLen = temp.length();
                } 
            } 
        }

        return res;
    }

    private boolean isPalindrome(String p) {
        String reverse = new StringBuffer(p).reverse().toString();
        return p.equals(reverse);
    }

}
```

**Approach: Manacher's algorithm**

```
                 S: b a b a d
                 T: # b # a # b # a # d #
                 P: 0 0 0 0 0 0 0 0 0 0 0
C = 0;R = 0;    
i = 0;M = 0; =>  P: 0 0 0 0 0 0 0 0 0 0 0 
i = 1;M = 1; =>  P: 0 1 0 0 0 0 0 0 0 0 0 
i = 2:M =
```

1. Preprocessing:  Adding boundaries
   1. Create **T array** with twice the length of string **S **plus**1**
   2. Fill the T array with arbitrary character **\# **before and after a character
2. processing:   
   1. Create **P** array with same length of transformed array **T**  
   2. initialize center & right to 0

   1. traverse T array and fill P from 0..N

   2. 

3. Post processing: Removing boundaries
   1. Create T array with half the length of previously transformed char array
   2. Fill T array, every i by  i\*2+1 from transformed char array

```java
  class Solution {
     public String longestPalindrome(String s) {
       // base case
       if (s == null || s.length() <1) {
         return "";
       }
        // transform original string with arbitrary seperator      
        char[] t = addBoundaries(s.toCharArray());
        int[] p = new int[t.length]; 
        int center = 0;
        int right = 0;
        int m = 0; // for left boundary
        int n = 0; // for right boundary
        for (int i = 0; i < t.length; i++) {
          if (i > right) {
            p[i] = 0;
            m = i-1;
            n = i+1;
          } else {
            int mirror = center*2-i;
            if (p[mirror] < (right-i-1)) {
              p[i] = p[mirror];
              m = -1;
            } else {
              p[i] = right-i;
              n = right+1;
              m = i*2-n;
            }
        }

        while (m >= 0 && n < t.length && t[m] == t[n]) {
          p[i]++;
          m--;
          n++;
        }

        if ((i+p[i]) > right) {
          center = i;
          right = i + p[i];
        }
       }

       // Calculate MAX Length
       int maxLen = 0;
       center = 0;
       for (int i = 0; i< t.length; i++) {
         if (maxLen < p[i]) {
           maxLen = P[i];
           center = i;
         }
       }

        char[] res = Arrays.copyOfRange(t, center-maxLen, center+maxLen+1);
        return String.valueOf(removeBoundaries(res));
     }

     private char[] addBoundaries(char[] s) {
       if (s == null || s.length < 1) {
          return "##".toCharArray();
        }
    
        int n = s.length;
        char[] T = new char[2*n + 1];
    
        for (int i = 0, j = 0; j < T.length && i < n; i++, j += 2) {
          T[j] = '#';
          T[j+1] = s[i];       
        }
        T[T.length-1] = '#';
    
        return T;
     }
     // transform '#a#b#a' => 'aba'
     // 
     private char[] removeBoundaries(char[] s) {
       // base case
       if (s == null || s.length < 1) {
         return "".toCharArray();
       }

       char[] t = new char[(s.length-1)/2];

       for (int i = 0; i < t.length; i++) {
         t[i] = s[i*2+1];
       }

       return t;
     }
```

```
String S = "babad";

1. preprocessing
       int N = S.length(); // 5
       char[] T = new char[2*N+1]; // #b#a#b#a#d#

       int[] P =
```



