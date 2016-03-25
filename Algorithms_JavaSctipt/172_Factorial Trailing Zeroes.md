##172. Factorial Trailing Zeroes
>Given an integer n, return the number of trailing zeroes in n!.

>Note: Your solution should be in logarithmic time complexity.


求出计算n！并求出结果后0的个数，需要考虑时间复杂度。

**分析：**本题如果不考虑时间复杂度，可使用暴力算法先求出n！的结果，再统计结果之后0的个数，但是暴力算法的时间复杂度会超过本题要求的时间限制，故只能采用技巧求出0的个数。

使用分解因数：阶乘情况下，结果0的出现只受2和5相乘的影响：2*5=10,也就是说0的个数取决于n！分解因数后2或5的个数：

	n！=2^x * 3^y * 4^z * 5^k *......

事实上，2的个数x总是小于5的个数k，故0的个数只受5的个数k的影响。

	/**
	 * @param {number} n
	 * @return {number}
	 */
	var trailingZeroes = function(n) {
	    var r = 0;
	    while(n > 1) {
			//对n进行分解，求出因数5的个数
	        r += Math.floor(n /= 5);
	    }
	    return r;
	};