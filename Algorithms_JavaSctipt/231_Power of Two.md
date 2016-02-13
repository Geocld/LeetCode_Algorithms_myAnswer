##231. Power of Two
Given an integer, write a function to determine if it is a power of two. 

判断一个数是否是2的乘方数。

**分析：**原理和方法与*326. Power of Three*一致，此处不再重复，直接上代码：

	/**
	 * @param {number} n
	 * @return {boolean}
	 */
	var isPowerOfTwo = function(n) {
	    return (Math.log10(n) / Math.log10(2)) % 1 == 0;
	};