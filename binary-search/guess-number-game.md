We are playing the Guess Game. The game is as follows:

I pick a number from**1**to**n**. You have to guess which number I picked.

Every time you guess wrong, I'll tell you whether the number is higher or lower.

You call a pre-defined API`guess(int num)`which returns 3 possible results \(-1, 1, or 0\):

**Example**

n = 10, I pick 4 \(but you don't know\)

Return 4. Correct !

```java
/* The guess API is defined in the parent class GuessGame.
   @param num, your guess
   @return -1 if my number is lower, 1 if my number is higher, otherwise return 0
      int guess(int num); */

public class Solution extends GuessGame {
    /**
     * @param n an integer
     * @return the number you guess
     */
    public int guessNumber(int n) {
        int start = 1;
        int end = n;
    
        while (start <= end) {
            
            int mid = start + ((end-start)/2);
            int guess = guess(mid);
            
            if (guess == 0) {
                return mid;
            } else if (guess < 0) {
                end = mid-1;
            } else {
                start = mid+1;
            }
            
        }
        
        return -1;
    }
}
```



