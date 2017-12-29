Write a function that takes an unsigned integer and returns the number of`1`bits it has.

**Example:**

The 32-bit integer`11`has binary representation

```
00000000000000000000000000001011

```

so the function should return`3`.

_Note that since Java does not have unsigned int, use long for Java_

```java
public class Solution {
	public int numSetBits(long a) {
	    int count = 0;
	    for (int i = 1; i < 33; i++) {
	        if (getBit(a, i) == true) {
	            count++;
	        }
	    }
	    
	    return count;
	}
	
	private boolean getBit(long n, int i) {
	    return (n & (1 << i)) != 0;
	}
}

```



