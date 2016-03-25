##102. Binary Tree Level Order Traversal
>Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).

>For example:
Given binary tree {3,9,20,#,#,15,7},
>
	    3
	   / \
	  9  20
	    /  \
	   15   7

>return its level order traversal as:
>
	[
	  [3],
	  [9,20],
	  [15,7]
	]

**分析：**求出二叉树每个深度下的节点，保存在一个二维数组中。针对二叉树问题使用一贯的递归遍历方法。

	/**
	 * Definition for a binary tree node.
	 * function TreeNode(val) {
	 *     this.val = val;
	 *     this.left = this.right = null;
	 * }
	 */
	/**
	 * @param {TreeNode} root
	 * @return {number[][]}
	 */
	var levelOrder = function(root) {
	    var result = [];
	    if (!root) return result;
	    Helper(root, result, 0);
	    return result;
	};
	//使用辅助函数helper，将每个深度的元素放在对应深度的数组中。
	var Helper = function(root, result, n) {
	    if (!root) return;
	    
	    if (result.length < n+1) {
	        var temp = [];
	        temp.push(root.val);
	        result.push(temp);
	    }
	    else {
	        result[n].push(root.val);
	    }
	    Helper(root.left, result, n+1);
	    Helper(root.right, result, n+1);
	}