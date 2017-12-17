Given a string**s**, find the longest palindromic substring in **s**. You may assume that the maximum length of **s **is 1000.

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

1. Preprocessing:  Adding boundaries
   1. Create **T array** with twice the length of string **S **plus**1**
   2. Fill the T array with arbitrary character **\# **before and after a character
2. processing: 
   1. Create **P** array with same length of transformed array **T**
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
     }
     
     private char[] addBoundaries(char[] s) {
       // base case
       if (s == null || s.length < 1) {
         return "##".toCharArray();
       }
       int n = s.length;
       char[] t = new char[2*N+1];
       
       for (int i = 0; i < s.length; i += 2) {
          t[i] = '#';
          t[i+1] = s[i];
       }
       
       // add last boundary
       t[t.length-1] = '#';
       
       return t;
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



