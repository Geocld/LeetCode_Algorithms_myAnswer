##83. Remove Duplicates from Sorted List
>Given a sorted linked list, delete all duplicates such that each element appear only once.

>For example,
Given `1->1->2`, return `1->2`.
Given `1->1->2->3->3`, return `1->2->3`. 

链表去重，然后输出新链表。

**分析：**链表遍历需从链表头部开始，遍历过程中，如当前节点与下一节点值相同，则将当前链表指针指向下下个节点，一次遍历即可完成所有操作，时间复杂度O(n).

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
	var deleteDuplicates = function(head) {
	    if (head === null || head.next === null) {
	        return head;
	    }
	    var p = head;
	    while (p !== null && p.next !== null) {
	        if (p.val === p.next.val) {
			//当前节点的值等于下一个节点的值，指针指向下下的节点。
	            p.next = p.next.next;
	        }
	        else {
	            p = p.next;
	        }
	    }
	    return head;
	};