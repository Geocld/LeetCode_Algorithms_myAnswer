##70. Climbing Stairs
>You are climbing a stair case. It takes n steps to reach to the top.

>Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top? 

有一个n阶的梯子，每次可以踩1步或2步，到达梯子顶部一共有几种不同的方法。

**分析：**f(n)为爬到第n阶梯子的不同方法，为了爬到第n阶，有两种方法：

1.从第n-1阶前进1步；

2.从第n-2阶前进2步。

因此有f(n) = f(n - 1) + f(n - 2).

实际上这是一个`斐波那契数列(Fibonacci formula)`问题。

	/**
	 * @param {number} n
	 * @return {number}
	 */
	var climbStairs = function(n) {
	    var step_a = 1,//到达i-1阶的方法数量
	        step_b = 0,//到达i-2阶的方法数量
	        step_c = 0;//到达当前i阶的方法
		//采用迭代的方式进行计算，时间复杂度O(n),空间复杂度O(1)
	    for (var i = 0; i < n; i++) {
	        step_c = step_a + step_b;
	        step_b = step_a;
	        step_a = step_c;
	    }
	    return step_c;
	};