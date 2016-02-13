##326. Power of Three
>Given an integer, write a function to determine if it is a power of three.

>Follow up:
Could you do it without using any loop / recursion? 

判断一个数是否是3的乘方数（不使用循环和递归）。

**分析：**如果N是3的乘方数，那么有如下计算规律：
	
    因为：3^X == N
    所以：log (3^X) == log N
    所以：X log 3 == log N
    所以：X == (log N) / (log 3)
    所以：X 必须是整数

由于此题在进行X的计算时涉及到小数，故还涉及到程序设计语言的`小数精度问题`，故本题在进行`log`运算时，采用了`log10`运算:

	/**
	 * @param {number} n
	 * @return {boolean}
	 */
	var isPowerOfThree = function(n) {
	    return (Math.log10(n) / Math.log10(3)) % 1 == 0;
	};

也可以看下此题如果采用递归或循环的计算:

递归版本

	var isPowerOfThree = function(n) {
	    return n > 0 && (n === 1 || n % 3 === 0 && isPowerOfThree(n/3))；
	};

循环版本

	var isPowerOfThree = function(n) {
	    if (n > 1) {
			while(n % 3 === 0) {
				return n === 1;
			}
		}
	};