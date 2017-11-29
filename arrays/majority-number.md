Given an array of integers, the majority number is the number that occurs`more than half`of the size of the array. Find it.

##### Notice

You may assume that the array is non-empty and the majority number always exist in the array.

**Example**

Given`[1, 1, 1, 1, 2, 2, 2]`, return`1`

[**Challenge**](http://www.lintcode.com/en/problem/majority-number/#challenge)

O\(_n_\) time and O\(_1_\) extra space



##### Approach : HashMap

```java
    /*
     * @param nums: a list of integers
     * @return: find a  majority number
     */
    public int majorityNumber(List<Integer> nums) {
        int majority = nums.size()/2;
        Map<Integer, Integer> map = new HashMap<>();
        for(int i = 0; i < nums.size(); i++) {
            int count = 1;
            int num = nums.get(i);
            if (map.containsKey(num)) {
                count += map.get(num);
            }
            
            map.put(num, count);
            
            if (map.get(num) > majority) {
                return num;
            }
        }
        
        return -1;
    }
```



