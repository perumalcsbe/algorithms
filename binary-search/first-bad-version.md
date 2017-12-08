The code base version is an integer start from 1 to n. One day, someone committed a bad version in the code case, so it caused this version and the following versions are all failed in the unit tests. Find the first bad version.

You can call`isBadVersion`to help you determine which version is the first bad one. The details interface can be found in the code's annotation part.

##### Notice

Please read the annotation in code area to get the correct way to call isBadVersion in different language. For example, Java is`SVNRepo.isBadVersion(v)`

**Example**

Given n =`5`:

```
isBadVersion(3) -> false
isBadVersion(5) -> true
isBadVersion(4) -> true
```

Here we are 100% sure that the 4th version is the first bad version.

```java
/**
 * public class SVNRepo {
 *     public static boolean isBadVersion(int k);
 * }
 * you can use SVNRepo.isBadVersion(k) to judge whether 
 * the kth code version is bad or not.
*/

public class Solution {
    /*
     * @param n: An integer
     * @return: An integer which is the first bad version.
     */
    public int findFirstBadVersion(int n) {
        int start = 1;
        int end = n;
        while (start <= end) {
            int mid = start+((end-start)/2);
            if (SVNRepo.isBadVersion(mid)) {
                end = mid - 1;
            } else {
                start = mid + 1;
            }
        }


        return start;
    }
}
```

```js
/**
 * Definition for isBadVersion()
 * 
 * @param {integer} version number
 * @return {boolean} whether the version is bad
 * isBadVersion = function(version) {
 *     ...
 * };
 */

/**
 * @param {function} isBadVersion()
 * @return {function}
 */
var solution = function(isBadVersion) {
    /**
     * @param {integer} n Total versions
     * @return {integer} The first bad version
     */
    return function(n) {
          let left = 1; 
          let right = n;

          while(left < right) {  
            let mid = left + ((right - left) >>> 1);
            if (isBadVersion(mid)) {
              right = mid; 
            } else {
              left = mid + 1;
            }
          }
          return left;
    };
};
```



