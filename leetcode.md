07-May Daily Leetcode
# 2816. Double a Number Represented as a Linked List

#### You are given the head of a non-empty linked list representing a non-negative integer without leading zeroes.
#### Return the head of the linked list after doubling it.

 
## Example 1:

#   1->8->9

### Input: head = [1,8,9]
### Output: [3,7,8]
### Explanation: The figure above corresponds to the given linked list which represents the number 189. Hence, the returned linked list represents the number 189 * 2 = 378.

## Example 2:

# 9->9->9

### Input: head = [9,9,9]
### Output: [1,9,9,8]
### Explanation: The figure above corresponds to the given linked list which represents the number 999. Hence, the returned linked list reprersents the number 999 * 2 = 1998. 
 

## Constraints:

### The number of nodes in the list is in the range [1, 104]
### 0 <= Node.val <= 9
### The input is generated such that the list represents a number that does not have leading zeros, except the number 0 itself.


# Approach
  According to the question we have a linked list 
  Let's take a Example
  ```
 7->8->9
```
  and we have to multiply by 2 and 
  return the corresponding on the shape of the linked list 
  like 789 * 2 = 1578
  Output:
  ```
1->5->7->8
```
So now the question is how I achieve this there are many ways but I want to discuss a beginner approach that is 
Let's reverse the list now the list is 
```
 7 <- 8 <- 9
```
now we traverse the linked list and multiply by 2 on every value of the node 
so in
## STEP - 1   
```
  9 * 2 = 18
```
but think we can check there we got sum 8 and a carry that is 1 so now we will change the sum with the previous node value

### SUM = 8 and CARRY = 1
```
 Result List:
  8->
```

## STEP - 2

```
  8 * 2 = 16 and we have to carry 1
```
  now, 16 + 1 = 17
  ### SUM = 7 and CARRY = 1
  ```
 Result List:
  8->7
```

## STEP-3
```
  7 * 2 = 14 and we have to carry 1
```
now, 14 + 1 = 15
### SUM = 5 and CARRY = 1
```
 Result List:
  8->7->5
```
now we can see we traverse the full linked list but still, there is a carry left so finally the last carry we will add to the result list :
```
 Result List:
  8-> 7 -> 5 -> 1
```
now we have to reverse the list because in first we reverse the list to multiply 2 from backward.


# Complexity
- Time complexity:
- Reversing the linked list: `O(n)`
- Traversing through the reversed list to double values: `O(n)`
- Reversing the modified list again: `O(n)`
#### Hence, the overall time complexity is O(n).

- Space complexity:

- The space complexity is primarily determined by the additional space required for the reversal of the linked list. Since we are using a constant amount of extra space for each node during the reversal process, - the space complexity for reversal is `O(1)`.
- Additionally, there is a `constant amount of extra space` required for variables like `carry`, `prev`, and `dummy`, irrespective of the size of the input list.
#### Therefore, the overall space complexity is also O(1).

# Code
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode doubleIt(ListNode head) {
        if( head == null) return null;
        ListNode reversed = reverse(head);
        ListNode current = reversed;
        ListNode prev = null;
        int carry = 0;
        while( current != null){
            int afterMul = current.val * 2 + carry;
            current.val = afterMul % 10;
            carry = afterMul / 10;
            prev = current;
            current = current.next;
        }
        if(carry > 0){
            ListNode lastNode = new ListNode(carry);
            prev.next = lastNode;
        }
        return reverse(reversed);
    }
    ListNode reverse(ListNode head){
        ListNode dummy = null;
        while( head != null){
            ListNode next = head.next;
            head.next = dummy;
            dummy = head;
            head = next;
        }
        return dummy;
    }
}
```


For more content like this, follow my GitHub and LinkedIn profiles:

<a href="https://github.com/subhadip-hazra">GitHub </a> </br>
<a href="https://www.linkedin.com/in/subhadiphazra/">Linkedin </a>
