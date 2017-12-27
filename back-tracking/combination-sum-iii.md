Find all possible combinations of **k **numbers that add up to a number **n**, given that only numbers from 1 to 9 can be used and each combination should be a unique set of numbers.

**Example 1:**

Input: **k**= 3, **n**= 7

Output:

```
[[1,2,4]]
```

**Example 2:**

Input: **k **= 3, **n **= 9

Output:

```
[[1,2,6], [1,3,5], [2,3,4]]
```

```java
class Solution {
    public List<List<Integer>> combinationSum3(int k, int n) {
        ArrayList<List<Integer>> list = new ArrayList<List<Integer>>();
        if (k <= 0 || n < k) {
            return list;
        }

        ArrayList<Integer> set = new ArrayList<>();
        dfs(n, k, 1, set, list);
        return list;
    }

    private void dfs(int n, int k, int start, ArrayList<Integer> set, ArrayList<List<Integer>> list) {
        if (set.size() == k && n == 0) {
            list.add(new ArrayList<Integer>(set));
            return;
        }

        for (int i = start; i <= 9; i++) {
            set.add(i);
            dfs(n-i, k, i+1, set, list);
            set.remove(set.size()-1);
        }
    }
}
```



