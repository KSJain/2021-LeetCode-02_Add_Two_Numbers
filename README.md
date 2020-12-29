# 2021-LeetCode-02_Add_Two_Numbers
This is a simple solution to the famous "Add Two Numbers" of a reversed Linked List problem. If you like feel free to download and tinker with the XCode Playground file from my Github repository link https://github.com/KSJain/2021-LeetCode-02_Add_Two_Numbers

I would be perodically keep solving as many questions as I could, to keep everyday interesting. I miss school days.

##### As of posting date the Stats are as following #####
**Runtime**: 44 ms, faster than 76.17% of Swift online submissions for Add Two Numbers.
**Memory Usage**: 13.7 MB, less than 82.64% of Swift online submissions for Add Two Numbers.
**Big-O Time Complexity**: O(n)

Feel free to comment and/or improve. I would like to learn and improve alongside my peers : )

##### Happy Coding #####

```
func addTwoNumbers(_ l1: ListNode?, _ l2: ListNode?) -> ListNode? {
    guard l1 != nil && l2 != nil else { return nil }
    
    var resultTail  = ListNode()
    let resultHead  = resultTail
    
    var list1       = l1,
        list2       = l2
    
    var carry       = 0
    
    while list1 != nil && list2 != nil {
        
        let sum         = (list1?.val ?? 0) + (list2?.val ?? 0) + carry
        carry           = sum > 9 ? 1 : 0
        
        let newNode     = ListNode(sum > 9 ? sum - 10 : sum)
        resultTail.next = newNode
        resultTail      = newNode
        
        list1           = list1?.next
        list2           = list2?.next
    }
    
    var leftover = list1 != nil ? list1 : list2
    
    while leftover != nil {
        
        let sum         = carry + (leftover?.val ?? 0)
        carry           = sum > 9 ? 1 : 0
        
        let newNode     = ListNode(sum > 9 ? sum - 10 : sum)
        resultTail.next = newNode
        resultTail      = newNode
        
        leftover        = leftover?.next
    }
    
    if carry == 1 {
        resultTail.next = ListNode(1)
    }
    
    return resultHead.next
}
```

Code in a nutshell:
1. guard check if list1 and list2 are **BOTH** non-nil. Otherwise return nil
2. we make result -  head and tail. As wedont wont change head its a constant and at this point headand tail are the same.
3. we copy l1 and l2 into local  list *variables*
4. conditionally loop as long as both list1 and list2 are not-nil
5. within the loop - 
	a. add list1, list2 digits and carry digit
	b. update the carry value
	c. create new node and update the tail of result
	d. move to next node in list 1 and 2
6. Stepping out of  first loop we make sure **if** there  are any leftover list digits
7. If any leftovers - second loop until  there  are no more leftover digits
8. within 2nd  loop  -
	a. add leftover digit and carry digit
	b. update the carry value
	c. create new node and update the tail of result
	d. move to next node in leftover
9. Finally we  make sure there  are no carry value. If any we  add that as a  new node to the  tail.
10. Return the reference to node containing the result

*Personally when I was solving the problem - I  made a few mistakes and decided to  treat them lessons (edge cases) and  adapted my code. I am hoping as I  solve more problems I would be able to account  for them or the likes in advance.*

It is noteworthy that the problem mentions that digits are  lined according to the power of 10. i.e: if you move one node distance in both list. you will have the value *  10(power of position -1)

**If you like - come to my page https://codinginferno.com/ for more fun learning. I love to learn while sharing, so feel free to ask.**
