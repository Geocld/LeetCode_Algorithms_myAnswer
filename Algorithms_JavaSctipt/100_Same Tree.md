##100. Same Tree
> Given two binary trees, write a function to check if they are equal or not.

>Two binary trees are considered equal if they are structurally identical and the nodes have the same value. 

对两个二叉树进行比较，判断是否相同。

**分析：**二叉树相同需要满足两个条件：

1.对应的树节点值相等；

2.树结构完全相同。

	/**
	 * Definition for a binary tree node.
	 * function TreeNode(val) {
	 *     this.val = val;
	 *     this.left = this.right = null;
	 * }
	 */
	/**
	 * @param {TreeNode} p
	 * @param {TreeNode} q
	 * @return {boolean}
	 */
	var isSameTree = function(p, q) {
	    if (p === null && q === null) {
	        return true;
	    }
	    else if((p === null && q !== null) || (p !== null && q === null)) {
	        return false;
	    }
	    if (p.val !== q.val) {
	        return false;
	    }
	    var is_left, is_right;
	    is_left = isSameTree(p.left, q.left);
	    is_right = isSameTree(p.right, q.right);
	    if(is_left && is_right) {
	        return true;
	    }//左右树节点完全相同时才返回true
	    else {
	        return false;
	    }
	};