Given two integers n and k, return all possible combinations of k numbers out of 1 ...n.

For example,  
If n= 4 and k= 2, a solution is:

```
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]
```

**Approach: Recursive DFS**

```java
class Solution {
    public List<List<Integer>> combine(int n, int k) {
        ArrayList<List<Integer>> list = new ArrayList<List<Integer>>();
        if (k <= 0 || n < k) {
            return list;
        }

        ArrayList<Integer> set = new ArrayList<>();
        dfs(n, k, 1, set, list);

        return list;
    }

    private void dfs(int n, int k, int start, ArrayList<Integer> set, ArrayList<List<Integer>> list) {
        // base case
        if (set.size() == k) {
            ArrayList<Integer> temp = (ArrayList<Integer>) set.clone();
            //ArrayList<Integer> temp = new ArrayList<Integer>(set);
            list.add(temp);
            return;
        }

        for (int i = start; i <= n; i++) {
            set.add(i);
            dfs(n, k, i+1, set, list);
            set.remove(set.size()-1);
        }
    }
}
```



