##206. Reverse Linked List
Reverse a singly linked list.

反转一个单向链表。

**分析：**反转单向链表不仅要将值反转，还需将指针反转，很简单的原理，直接看代码。


	/**
	 * Definition for singly-linked list.
	 * function ListNode(val) {
	 *     this.val = val;
	 *     this.next = null;
	 * }
	 */
	/**
	 * @param {ListNode} head
	 * @return {ListNode}
	 */
	var reverseList = function(head) {
	    var last = null;
	    while (head !== null) {
			//取临时变量temp，将前后的节点进行对调
	        var temp = head.next;
	        head.next = last;
	        last = head;
	        head = temp;
	    }
	    return last;
	};