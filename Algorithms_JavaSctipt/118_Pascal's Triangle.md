##118. Pascal's Triangle
>Given numRows, generate the first numRows of Pascal's triangle.

>For example, given numRows = 5,
Return
>
	[
	     [1],
	    [1,1],
	   [1,2,1],
	  [1,3,3,1],
	 [1,4,6,4,1]
	]

给出一个整数，输出整数对应的前几行`杨辉三角(Pascal's Triangle)`。

**分析：**`杨辉三角(Pascal's Triangle)`使用wiki的一个图解可以清楚的了解到他的算法规律：

![](http://i.imgur.com/MXSebwL.gif)

杨辉三角每一行的元素都是基于上一行的元素之和，本题解法如下：

	/**
	 * @param {number} numRows
	 * @return {number[][]}
	 */
	var generate = function(numRows) {
	    if (numRows === 0) {
	        return [];
	    }
	    var triangle = [[1]], tier;
		//外循环控制杨辉三角的行数
	    for (var i = 0; i < numRows - 1; i++) {
	        tier = [1];
	        for(var j = 1; j < triangle[i].length; j++) {
	            tier[j] = triangle[i][j] + triangle[i][j - 1];
	        }
	        tier.push(1);
	        triangle.push(tier);
	    }
	    return triangle;
	};

参考资料：

[Pascal's_triangle](https://en.wikipedia.org/wiki/Pascal's_triangle)
