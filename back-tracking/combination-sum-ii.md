Given a collection of candidate numbers \(**C**\) and a target number \(**T**\), find all unique combinations in **C **where the candidate numbers sums to **T**.

Each number in**C**may only be used**once**in the combination.

**Note:**

* All numbers \(including target\) will be positive integers.
* The solution set must not contain duplicate combinations.

For example, given candidate set`[10, 1, 2, 7, 6, 1, 5]`and target`8`,  
A solution set is:

```
[
  [1, 7],
  [1, 2, 5],
  [2, 6],
  [1, 1, 6]
]
```

---

```java
class Solution {
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        ArrayList<List<Integer>> list = new ArrayList<List<Integer>>();

        // base case
        if (candidates == null || candidates.length < 1) {
            return list;
        }
        // sort candidates O(nlogn)
        Arrays.sort(candidates);

        ArrayList<Integer> set = new ArrayList<Integer>();
        dfs(candidates, target, 0, set, list);

        return list;
    }

    private void dfs(int[] candidates, int target, int start, ArrayList<Integer> set, ArrayList<List<Integer>> list) {
        // base case
        if (target == 0) {
            ArrayList<Integer> temp = new ArrayList<Integer>(set);
            list.add(temp);
            return;
        }
        if (target < 0) {
            return;
        }
        int prev = -1; // to avoid duplicates 
        for(int i = start; i < candidates.length; i++) {
            if (prev != candidates[i]) {
                set.add(candidates[i]);
                dfs(candidates, target-candidates[i], i+1, set, list);
                set.remove(set.size()-1);
                prev = candidates[i];
            }
        }
    }
}
```



