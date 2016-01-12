##237. Delete Node in a Linked List
> Write a function to delete a node (except the tail) in a singly linked list, given only access to that node.<br>
Supposed the linked list is 1 -> 2 -> 3 -> 4 and you are given the third node with value 3, the linked list should become 1 -> 2 -> 4 after calling your function. 

给一个单链表，通过指定的节点对链表节点进行删除。

**分析：**单链表的删除只要满足节点删除时，当前节点的上个节点的值为下一个节点的值，当前节点上个节点的指针指向下下个指针，如图所示：

![](http://i.imgur.com/nkpKgBm.jpg)


	/**
	 * Definition for singly-linked list.
	 * function ListNode(val) {
	 *     this.val = val;
	 *     this.next = null;
	 * }
	 */
	/**
	 * @param {ListNode} node
	 * @return {void} Do not return anything, modify node in-place instead.
	 */
	var deleteNode = function(node) {
	    node.val = node.next.val;
	    node.next = node.next.next;
	};