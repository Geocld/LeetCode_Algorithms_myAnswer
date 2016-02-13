##198. House Robber
>You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

>Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

盗窃者对一条街道进行盗窃，其中不能连续盗窃相邻的屋子，求出可以盗窃出来的最大金额。

**分析：**此题实际上是使用`DP思想`，在[70. Climbing Stairs](https://github.com/Geocld/LeetCode_Algorithms_myAnswer/blob/master/Algorithms_JavaSctipt/70_Climbing%20Stairs.md)一题中也使用了类似的思想，`DP思想`即'动态规划思想'，就是解决多阶段决策过程最优化问题的一种常用方法。'动态规划'的基本思想是：将待解决的问题分解为若干个相互联系的子问题，先求解子问题，然后根据子问题的解得到原问题的解。

在本题中，盗窃者面对的实际上是一个数组，如果当前元素被选择了，那么上一个元素必定是不选；如果当前元素不选，则上一个元素就无所谓选还是不选，在这里，使用变量`take`表示当前选择，使用`notake`表示当前不选，`maxprofit`表示当前的最大利润。

如果当前take，则take的和就是上一次的maxprofit加上当前数；如果当前为notake，则当前的和就是上一个maxprofit，故通过一次遍历即可求解出最优解，时间复杂度为O(N)。

	/**
	 * @param {number[]} nums
	 * @return {number}
	 */
	var rob = function(nums) {
	    var take = 0;
	    var notake = 0;
	    var maxprofix = 0;
	    for (var i = 0; i < nums.length; i++) {
	        take = notake + nums[i];//取值
	        notake = maxprofix;//不取值
	        maxprofix = Math.max(take, notake);//当前最大利润
	    }
	    return maxprofix;
	};