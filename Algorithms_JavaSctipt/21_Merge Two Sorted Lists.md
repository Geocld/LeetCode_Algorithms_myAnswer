##21. Merge Two Sorted Lists
Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

合并两个有序链表。

**分析：**合并两个有序链表，需要注意的是合并后生成的新链表也需要是有序的。

	/**
	 * Definition for singly-linked list.
	 * function ListNode(val) {
	 *     this.val = val;
	 *     this.next = null;
	 * }
	 */
	/**
	 * @param {ListNode} l1
	 * @param {ListNode} l2
	 * @return {ListNode}
	 */
	var mergeTwoLists = function(l1, l2) {
	    var new_list;
	    if (l1 === null) return l2;
	    if (l2 === null) return l1;
	    if (l1.val < l2.val) {
	        new_list = l1;
	        new_list.next = mergeTwoLists(l1.next, l2);
	    }
	    else {
	        new_list = l2;
	        new_list.next = mergeTwoLists(l1, l2.next);
	    }
	    return new_list;
	};