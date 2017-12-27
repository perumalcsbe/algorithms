Given a **set **of candidate numbers \(**C**\)**\(without duplicates\)**and a target number \(**T**\), find all unique combinations in **C **where the candidate numbers sums to **T**.

The **same **repeated number may be chosen from**C**unlimited number of times.

**Note:**

* All numbers \(including target\) will be positive integers.
* The solution set must not contain duplicate combinations.

For example, given candidate set`[2, 3, 6, 7]`and target`7`,  
A solution set is:

```
[
  [7],
  [2, 2, 3]
]
```

**Approach: DFS**

```java
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
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
        
        for(int i = start; i < candidates.length; i++) {
            // if value greater than target
            if (candidates[i] > target) {
                return;
            }
            
            set.add(candidates[i]);
            
            dfs(candidates, target-candidates[i], i, set, list);
            
            set.remove(set.size()-1);
        }
    }
}
```



