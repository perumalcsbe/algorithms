Given a string which contains only letters. Sort it by lower case first and upper case second.

##### Notice

It's \_NOT \_necessary to keep the original order of lower-case letters and upper case letters.

**Example**

For`"abAcD"`, a reasonable answer is`"acbAD"`

[**Challenge**](http://www.lintcode.com/en/problem/sort-letters-by-case/#challenge)

Do it in one-pass and in-place.

**Approach: Two Pointers**

```
Time Complexity: O(n)
Space Complexity: O(1)
```

```java
public class Solution {
    /*
     * @param chars: The letter array you should sort by Case
     * @return: nothing
     */
    public void sortLetters(char[] chars) {
        // base case
        if (chars == null || chars.length < 1) return;

        // two pointers
        int start = 0;
        int end = chars.length - 1;


        while (start < end) {

            // increment start if chars[start] = [a-z]
            while (start < end && Character.isLowerCase(chars[start])) {
                start++;
            }

             // decrement end if chars[end] = [A-Z]
            while (start < end && Character.isUpperCase(chars[end])) {
                end--;
            }

            if (start < end) {
                char temp = chars[start];
                chars[start] = chars[end];
                chars[end] = temp;
                start++;
                end--;
            }

        }
    }
}
```



