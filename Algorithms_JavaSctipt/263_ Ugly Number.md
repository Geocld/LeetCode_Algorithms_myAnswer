##263. Ugly Number
> Write a program to check whether a given number is an ugly number.

>Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 6, 8 are ugly while 14 is not ugly since it includes another prime factor 7.

>Note that 1 is typically treated as an ugly number. 

判断一个数是否是"丑数"，"丑数"的最小分解因数只能是2、3、5，如6和8是"丑数"(6 = 2 * 3; 8 = 2 * 2 * 2),但是14却不是"丑数"，因为14 = 2 * 7。

**分析：**"丑数"即只有3种最小因数2\3\5的数，用表达式即：

	Ugly Number = 2^n * 3^m * 5^k

因此，只要对指定数字使用2或3或5进行分解，最后到不能再分解时结果为1，这个数就是Ugly Number。

	/**
	 * @param {number} num
	 * @return {boolean}
	 */
	var isUgly = function(num) {
	    if (num === 0) {
	        return false;
	    }
	    if (num === 1) {
	        return true;
	    }
	    while (num % 2 === 0) {
	        num = num >> 1;
	    }
	    while (num % 3 === 0) {
	        num /= 3;
	    }
	    while (num % 5 === 0) {
	        num /= 5;
	    }
	    return num === 1;
	};