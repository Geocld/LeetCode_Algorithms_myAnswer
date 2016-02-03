##111. Minimum Depth of Binary Tree
>Given a binary tree, find its minimum depth.

>The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

求二叉树的最小深度。

**分析：**与[104. Maximum Depth of Binary Tree](https://github.com/Geocld/LeetCode_Algorithms_myAnswer/blob/master/Algorithms_JavaSctipt/104_%20Maximum%20Depth%20of%20Binary%20Tree.md)相似的原理，**这里的深度表示叶子节点到根节点的距离。比如[1, 2]的最小深度为2，而不是1**。通过递归遍历二叉树，通过对比左右树枝的深度，取当前最小的树枝深度，直到返回整个二叉树的最小深度。

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
	var minDepth = function(root) {
	    if (root === null) {
	        return 0;
	    }
	    else if (root.left === null && root.right === null) {
	        return 1;
	    }
	    else if (root.left !== null && root.right === null) {
	        return 1 + minDepth(root.left);
	    }
	    else if (root.left === null && root.right !== null) {
	        return 1 + minDepth(root.right);
	    }
	    else {
	        return 1 + Math.min(minDepth(root.left), minDepth(root.right));
	    }
	};

也可以将[104. Maximum Depth of Binary Tree](https://github.com/Geocld/LeetCode_Algorithms_myAnswer/blob/master/Algorithms_JavaSctipt/104_%20Maximum%20Depth%20of%20Binary%20Tree.md)的代码稍作修改，也可以得到正确答案：

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
	var minDepth = function(root) {
	    if (root === null) {
		        return 0;
		    }
		//未到达树节点末端时取左右节点中深度最小的深度
		if (root.left !== null && root.right !==null) {
		    return 1 + Math.min(minDepth(root.left), minDepth(root.right));
		}
		//到达树节点末端
		else {
		    return 1 + Math.max(minDepth(root.left), minDepth(root.right));
		}
	};
	