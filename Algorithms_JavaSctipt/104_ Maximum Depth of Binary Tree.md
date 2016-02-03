##104. Maximum Depth of Binary Tree

>Given a binary tree, find its maximum depth.<br>
The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

给定一个二叉树，求出二叉树的最大深度。

**分析：**通过递归遍历二叉树，每次返回该节点所在深度，左右树枝对比取得深度最大的一边，直到返回最大深度。

	/**
	 * Definition for a binary tree node.
	 * function TreeNode(val) {
	 *     this.val = val;
	 *     this.left = this.right = null;
	 * }
	 */
	/**
	 * @param {TreeNode} root
	 * @return {number}
	 */
	var maxDepth = function(root) {
	    var res = 1;
	    if (root === null){
	        return 0
	    }
	    res += max(maxDepth(root.left), maxDepth(root.right));
	    return res;
	};
	function max(a, b){
	    return a > b ? a : b;
	}