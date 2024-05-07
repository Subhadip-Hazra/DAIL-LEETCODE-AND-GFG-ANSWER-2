# 07-may Daily GFG

## Question
### Reverse Level Order Traversal (GFG)

Given a binary tree of size n, find its reverse level order traversal. ie- the traversal must begin from the last level.

### Example 1:

**Input** :
```
        1
      /   \
     3     2
```
**Output**: 
```
3 2 1
```
**Explanation**:
Traversing level 1 : 3 2
Traversing level 0 : 1

### Example 2:

**Input** :
```
       10
      /  \
     20   30
    / \ 
   40  60
```
**Output**: 
```
40 60 20 30 10
```
**Explanation**:
Traversing level 2 : 40 60
Traversing level 1 : 20 30
Traversing level 0 : 10

**Your Task:** 
You don't need to read input or print anything. Complete the function `reverseLevelOrder()` which takes the root of the tree as input parameter and returns a list containing the reverse level order traversal of the given tree.

**Expected Time Complexity:** O(n)
**Expected Auxiliary Space:** O(n)

**Constraints:**
1 ≤ n ≤ 10^4

## Java Solution
```
  class Tree
{
    public ArrayList<Integer> reverseLevelOrder(Node node) 
    {
        // code here
        ArrayList<Integer> list = new ArrayList<Integer>();
        if(node == null) return list;
        Queue<Node> q = new LinkedList<Node>();
        q.add(node);
        while( !q.isEmpty()){
            Node curr = q.poll();
            list.add(curr.data);
            if(curr.right != null) {
                q.add(curr.right);
            }
            if(curr.left != null) {
                q.add(curr.left);
            }
        }
        Collections.reverse(list);
        return list;
    }
}
```
# Time Complexity
Time complexity of this code is O(n) because we have to visit all the nodes

# Space Complexity
Space complexity of this code is O(n) because it depends on the number of nodes

# Explanation
According to the question, there is a tree we just have to traverse from backwards. What if we do not traverse backwards. Ok then we have two choices one choice is we can traverse by BFS or DFS algorithm. But DFS is not useful here because it covers the full depth then backtracks but we have to traverse on BFS. Ok let's traverse using BFS

Test case:
```
                                     result List  [ ]
       10__________________level 1                [ 10 ]
      /  \
     20   30_______________level 2                [ 10 , 20 , 30 ]
    / \ 
   40  60__________________level 3                [ 10, 20 , 30 , 40 , 60 ]
```

## Now we have this list [ 10 , 20 , 30 , 40 , 60 ]
now we have to reverse the list ( because we checking from forward the answer needs the backward traverse answer) after reversing the list will be [ 60 , 40 , 30 , 20 , 10 ]  
😞😞😞😞  WTF! The output does not match our current answer.

don't worry let's try with the BFS search but not left - > right, now we will try right - > left 

Test case:
```
                                     result List  [ ]
       10__________________level 1                [ 10 ]
      /  \
     20   30_______________level 2                [ 10 , 30 , 20 ]
    / \ 
   40  60__________________level 3                [ 10, 30 , 20 , 60 , 40 ]
```
## Now we have this list [ 10, 30 , 20 , 60 , 40 ]
now we have to reverse the list,
After reversing the list the list is [ 40 , 60 , 20 , 30 , 10 ] now it's matching with the answer.


For more content like this, follow my GitHub and LinkedIn profiles:

<a href="https://github.com/subhadip-hazra">GitHub </a> </br>
<a href="https://www.linkedin.com/in/subhadiphazra/">Linkedin </a>
