##191. Number of 1 Bits
>Write a function that takes an unsigned integer and returns the number of ’1' bits it has (also known as the Hamming weight).

>For example, the 32-bit integer ’11' has binary representation 00000000000000000000000000001011, so the function should return 3.

求出一个非负二进制中`1`的个数。

**分析：**本题为`汉明重量`问题，汉明重量是一串符号中非零符号的个数。本题有两种解题方案：

1.将数字转为数组，对每一个元素进行遍历，再统计数字1出现的次数。

2.基于一个事实：数字X与X-1进行与运算得到的最低位永远是0。

通常第二种方法速度会快很多。

	/**
	 * @param {number} n - a positive integer
	 * @return {number}
	 */
	var hammingWeight = function(n) {
	    var count = 0;
	    while (n) {
	        n = n & (n - 1);
	        count++;
	    }
	    return count;
	};

参考：

[汉明重量](https://zh.wikipedia.org/wiki/%E6%B1%89%E6%98%8E%E9%87%8D%E9%87%8F)