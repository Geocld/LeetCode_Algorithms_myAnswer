##202. Happy Number
>Write an algorithm to determine if a number is "happy".

>A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

>Example: 19 is a happy number

>1^2 + 9^2 = 82<br>
>8^2 + 2^2 = 68<br>
>6^2 + 8^2 = 100<br>
>1^2 + 0^2 + 0^2 = 1<br>

判断一个数是否是`Happy Number`。如果一个数，取各位数字进行乘方和运算，如果结果不是1，再将结果进行乘方和运算，直到结果为1,则这个数就是`Happy Number`。

**分析：**如果按照`Happy Number`的定义对数字进行单相暴力循环求解，因为不知道数字不是`Happy Number`时的最终情况，则此题无从下手。如果取一个非`Happy Number`，进行计算，会发现：非`Happy Number`的乘方和结果在一定阶段后会循环出现，如数字`2`：

	2^2 = 4
	4^2 = 16
	1^2+6^2 = 37
	3^2+7^2 = 58
	5^2+8^2 = 89
	8^2+9^2 = 145
	1^2+4^2+5^2 = 42
	4^2+2^2 = 20
	2^2 + 0^2 = 4
	4^2 = 16
	//以下循环运算乘方和结果将重复

故`Happy Number`的判断条件为：乘方和的结果不重复出现，在有限次的运算中最终乘方和结果为1。

在程序设计中，对已出现的运算结果跟踪，采用的是hash的字典遍历方法：

	/**
	 * @param {number} n
	 * @return {boolean}
	 */
	var isHappy = function(n) {
	    var map = {};//定义个map对象存储已出现的结果
	    var num;
	    while(!map[n]) {
			//将已出现的结果做为map对象的属性，属性值为true
	        map[n] = true;
	        num = 0;
	        while(n > 0) {
	            num += (n % 10) * (n % 10);
	            n = Math.floor(n / 10);
	        }
	        if (num === 1) return true;
	        n = num;
	    }
	    return false;
	};
