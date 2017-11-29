### Find the Duplicate Number

Given an array nums containing n+ 1 integers where each integer is between 1 and n \(inclusive\), prove that at least one duplicate number must exist. Assume that there is only one duplicate number, find the duplicate one.

**Note:**

1. You **must not **modify the array \(assume the array is read only\).
2. You must use only constant, O\(1\) extra space.
3. Your runtime complexity should be less than`O(n2)`.
4. There is only one duplicate number in the array, but it could be repeated more than once.

##### Approach 1: Using Map O\(n\) space

```js
function findDuplicate(arr) {
  let map = new Map();
  for(let i = 0; i < arr.length; i++) {
    let count = map.get(arr[i]) || 0;

    map.set(arr[i], ++count);
  }

  for(let [key, count] of map) {
      if (count > 1) {
      return key;
    }
  }

  return -1;
}
```

```java
    /*
     * @param nums: an array containing n + 1 integers which is between 1 and n
     * @return: the duplicate one
     */
    public int findDuplicate(int[] nums) {
        HashSet<Integer> set = new HashSet<Integer>();
        
        for(int i = 0; i < nums.length; i++) {
            if (set.contains(nums[i])) {
                return nums[i];
            } 
            
            set.add(nums[i]);
        }
        
        return -1;
    }
```

##### 

##### Approach 2: [Two Pointers](/two-pointers.md)

```

```

##### Approach 3: [Binary Search](/binary-search.md)

```

```



