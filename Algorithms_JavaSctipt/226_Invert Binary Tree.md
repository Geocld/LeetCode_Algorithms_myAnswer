##226. Invert Binary Tree
>Invert a binary tree.
>	
	     4
	   /   \
	  2     7
	 / \   / \
	1   3 6   9

>to

>
>	         4
	   /   \
	  7     2
	 / \   / \
	9   6 3   1

实现反转二叉树。

**分析：**这题是Google面试 Max Howell的面试题，可谓是放水题，但是Max Howell没有答上...

反转二叉树需要遍历二叉树，使用递归即可。

	/**
	 * Definition for a binary tree node.
	 * function TreeNode(val) {
	 *     this.val = val;
	 *     this.left = this.right = null;
	 * }
	 */
	/**
	 * @param {TreeNode} root
	 * @return {TreeNode}
	 */
	var invertTree = function(root) {
	    if (root === null) {
	        return root;
	    }
	    else {
	        var t;
	        t = root.left;
	        root.left = root.right;
	        root.right = t;
	        
	        invertTree(root.left);
	        invertTree(root.right);
	        return root;
	    }
	};