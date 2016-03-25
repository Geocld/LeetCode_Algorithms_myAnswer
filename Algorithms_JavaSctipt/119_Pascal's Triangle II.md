##119. Pascal's Triangle II
>Given an index k, return the kth row of the Pascal's triangle.

>For example, given k = 3,
Return [1,3,3,1]. 

>Note:
Could you optimize your algorithm to use only O(k) extra space? 

根据一个正整数，输出杨辉三角的指定行，要求在空间复杂度O(k)完成。

**分析：**本题和`118. Pascal's Triangle`都是求杨辉三角，而且本题结果也可以通过`118. Pascal's Triangle`求出，但是`118. Pascal's Triangle`的解法需要的空间复杂度为O(i*j),不符合本题的空间复杂度要求，故需要从另一个角度求出该题。

本题解法可根据杨辉三角的一个数学规律：对于杨辉三角的第K行，他的内部元素为：[C(K,0),C(K,1),C(K,2)...,C(K,K-1),C(K,K)],其中的C是排列组合中的无须排列,其中又有：

	C(K,i) = C(k,i-1) * (k-i+1)/i

在本题中，k是需要求解的行数，i是需要求解的行数中的第i个元素。

	/**
	 * @param {number} rowIndex
	 * @return {number[]}
	 */
	var getRow = function(rowIndex) {
	    if (rowIndex === 0) {
	        return [1];
	    }
	    var row_triangle = [1];
	    for (var i = 1; i <= rowIndex; i++) {
	        var temp = row_triangle[i - 1] * ((rowIndex - i + 1) / i);
	        row_triangle.push(temp);
	    }
	    return row_triangle;
	};