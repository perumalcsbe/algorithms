Given a non-empty string`s`, you may delete **at most **one character. Judge whether you can make it a palindrome.

**Example 1:**

```
Input:"aba"
Output:True
```

**Example 2:**

```
Input:"abca"
Output:True
Explanation: You could delete the character 'c'.
```

**Note:**

1. The string will only contain lowercase characters a-z. The maximum length of the string is 50000.

```
char[] dict = [0, 0 , 0, 0, 0] // 26
//aba         [0, 1] =>  
//abca        [0, 1, 1] =>
// abb        [1, 0]
```



