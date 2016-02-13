##110. Balanced Binary Tree
>Given a binary tree, determine if it is height-balanced.

>For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

判断二叉树是否是`平衡二叉树`。

**分析：**根据`平衡二叉树(AVL)`的定义，父节点的左子树和右子树的高度之差不能大于1，故解此题的关键是求出左子树和右子树的节点高度，比较左子树和右子树的高度差，若高度差大于1，则该二叉树不是平衡二叉树。

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
	var isBalanced = function(root) {
	    if (!root) return true;
		//如果左、右子树的高度差大于1，则不是平衡二叉树
	    if (Math.abs(height(root.left) - height(root.right)) > 1) {
	        return false;
	    }
		//节点不为空，则继续计算节点深度直到最后一个节点
	    return isBalanced(root.left) && isBalanced(root.right);
	};
	//求子节点高度
	function height(root) {
	    if (!root) {
	        return 0;
	    }
	    else {
	        var l = height(root.left);
	        var r = height(root.right);
	        return l > r ? (l + 1) : (r + 1);
	    }
	}