##235. Lowest Common Ancestor of a Binary Search Tree

>Given a binary search tree (BST), find the lowest common ancestor (LCA) of two given nodes in the BST. 

>
			_______6______
	       /              \
	    ___2__          ___8__
	   /      \        /      \
	   0      _4       7       9
	         /  \
	         3   5
>For example, the lowest common ancestor (LCA) of nodes 2 and 8 is 6. Another example is LCA of nodes 2 and 4 is 2, since a node can be a descendant of itself.

给出一个`查询二叉树(Binary Search Tree)`,找出两个节点的最近公共父节点(LCA),如LCA（3,5）=4，LCA(3,9)=6,LCA(5,0)=2，LCA(2,4)=2。

分析：本题指定只找出查询二叉树的LCA，查询二叉树是一种有特殊属性的二叉树数据结构，查找二叉树具备如下2个特性：

1.若任意节点的左子树不空，则左子树上所有结点的值均小于它的根结点的值；

2.任意节点的右子树不空，则右子树上所有结点的值均大于它的根结点的值；

利用这两个特性，查找LCA时：

设当前节点为t,需要查找的节点为u和v。

1.如果当前节点t小于u，v，则u，v都在t的左侧，因此u，v的LCA必定在t的左子树中，故从t的左子树中继续查找；

2.如果当前节点t大于u，v，则u，v都在t的右侧，因此u，v的LCA必定在t的右子树中，故从t的右子树中继续查找；

3.如果满足u < t < v，那么t为u，v的LCA,返回t。

实现代码如下：

	/**
	 * Definition for a binary tree node.
	 * function TreeNode(val) {
	 *     this.val = val;
	 *     this.left = this.right = null;
	 * }
	 */
	/**
	 * @param {TreeNode} root
	 * @param {TreeNode} p
	 * @param {TreeNode} q
	 * @return {TreeNode}
	 */
	var lowestCommonAncestor = function(root, p, q) {
	    if(root === null) {
	        return root;
	    }
	    
	    if(root === p || root === q) {
	        return root;
	    }
	    
		//p，q节点都小于root节点，继续在root.left中查找
	    if(root.val > p.val && root.val > q.val){
	        return lowestCommonAncestor(root.left, p, q);
	    } 
		//p，q节点都大于root节点，继续在root.left中查找
	    else if (root.val < p.val && root.val < q.val) {
	        return lowestCommonAncestor(root.right, p, q);
	    }
		//满足p < root < q，当前root即为LCA。
	    else {
	        return root;
	    }
	};


参考资料:

[Lowest common ancestor](https://en.wikipedia.org/wiki/Lowest_common_ancestor)

[二叉搜索树](https://zh.wikipedia.org/wiki/%E4%BA%8C%E5%85%83%E6%90%9C%E5%B0%8B%E6%A8%B9)

[最近公共祖先LCA问题](https://github.com/julycoding/The-Art-Of-Programming-By-July/blob/master/ebook/zh/03.03.md)