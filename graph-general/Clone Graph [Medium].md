Problem: https://leetcode.com/problems/clone-graph/?envType=study-plan-v2&envId=top-interview-150

```
/*
// Definition for a Node.
class Node {
    public int val;
    public List<Node> neighbors;
    public Node() {
        val = 0;
        neighbors = new ArrayList<Node>();
    }
    public Node(int _val) {
        val = _val;
        neighbors = new ArrayList<Node>();
    }
    public Node(int _val, ArrayList<Node> _neighbors) {
        val = _val;
        neighbors = _neighbors;
    }
}
*/

class Solution {
    public Node cloneGraph(Node node) {
        if(node!=null) {
            Map<Integer, Node> oldToNew = new HashMap<>();
            return dfs(node, oldToNew);
        }

        return node;
    }

    Node dfs(Node node, Map<Integer, Node> oldToNew) {
        if(oldToNew.containsKey(node.val)) {
            return oldToNew.get(node.val);
        }

        Node copy = new Node(node.val);
        oldToNew.put(copy.val, copy);

        for(Node n: node.neighbors) {
            copy.neighbors.add(dfs(n, oldToNew));
        }
        return copy;
    }
}
```
