##13. Roman to Integer
>Given a roman numeral, convert it to an integer.

>Input is guaranteed to be within the range from 1 to 3999.

将罗马数字转换为阿拉伯数字，输出1到3999即可。

**分析：**罗马数字共有7个，即I（1）、V（5）、X（10）、L（50）、C（100）、D（500）和M（1000）,将1-3000的罗马数字罗列如下：
![](http://i.imgur.com/m6VdXfj.jpg)
可以发现规律：罗马数字即是在这7个基本数字的基础上，进行加法，如1、2、3的写法；另一个情况是5前后以及10前后的数字，在基本数字前加一位数或数字后加一位数。

实现代码如下：

	/**
	 * @param {string} s
	 * @return {number}
	 */
	var romanToInt = function(s) {
	    var a = {
	        'I': 1,
	        'V': 5,
	        'X': 10,
	        'L': 50,
	        'C': 100,
	        'D': 500,
	        'M': 1000
	    };
	    var num = 0;
	    s = s.split('');//将字符串转换为数组进行处理
	    for (var i = 0; i < s.length; i++) {
			//处理4、9、40、90、400、900的情况
	        if (a[s[0]] < a[s[1]] && s.length === 2) {
	            num = a[s[1]] - a[s[0]];
	            return num;
	        }
			//处理4、9、40、90、400、900基数出现在数字中间的情况
	        if (a[s[i]] < a[s[i+1]] && s.length > 2) {
	            num += a[s[i+1]] - a[s[i]];
	            i++;
	        }
	        else {
	            num += a[s[i]];
	        }
	    }
	    return num;
	};


