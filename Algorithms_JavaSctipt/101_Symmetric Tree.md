##101. Symmetric Tree
>Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

>For example, this binary tree is symmetric:
>
	    1
	   / \
	  2   2
	 / \ / \
	3  4 4  3

>But the following is not:
>
	    1
	   / \
	  2   2
	   \   \
	   3    3

判断二叉树是否是镜像二叉树。

**分析：**镜像二叉树通过遍历二叉树，比较左节点（p1）和右节点（p2）的值是否相等，直到最后一个节点，如满足`isSym(p1.left,p2.right) && isSym(p1.right,p2.left)`，则该二叉树是平衡二叉树。

	/**
	 * Definition for a binary tree node.
	 * function TreeNode(val) {
	 *     this.val = val;
	 *     this.left = this.right = null;
	 * }
	 */
	/**
	 * @param {TreeNode} root
	 * @return {boolean}
	 */
	var isSymmetric = function(root) {
	    if (root === null) {
	        return true;
	    }
	    else {
	        return isSym(root.left, root.right);
	    }
	};
	
	function isSym(p1, p2) {
	    if (p1 === null && p2 === null) {
	        return true;
	    }
	    else if (p1 !==null && p2 !== null) {
	        if (p1.val === p2.val) {
	            return isSym(p1.left,p2.right) && isSym(p1.right,p2.left);
	        }
	        return false;
	    }
	    else {
	        return false;
	    }
	}