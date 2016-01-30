##171. Excel Sheet Column Number
>Related to question Excel Sheet Column Title

>Given a column title as appear in an Excel sheet, return its corresponding column number.

>For example:
>
	A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 

本题是实现26进制的算法，将字母转换为对应的十进制阿拉伯数字。

**分析：**做这题前需要知道非十进制转十进制的算法，以16进制为例，算法如下：

(12)h = 1 * 16^1 + 2 * 16^0 = 10;

(3AB)h = 3 * 16^2 + A(10) * 16^1 + B(11) * 16^0 = 939;

换算原则即：`每一位数的权重乘进制数的位数次方(从0算起),将相应结果相加`。

回到本题的26进制算法上看，A代表的权重是1，B代表的权重是2...依次类推，Z代表的权重是26，AA、AB转十进制是算法如下：

AA = 1 * 26^1 + 1 * 26^0 = 27;

AB = 1 * 26^1 + 2 * 26^0 = 28;

故本题的解决方案如下：

	/**
	 * @param {string} s
	 * @return {number}
	 */
	var titleToNumber = function(s) {
	    var result = 0,
	        len = s.length;
	    for (var i = len - 1, j = 0; i >= 0, j < len; i--, j++) {
	        result += (s.charCodeAt(i) - 'A'.charCodeAt() + 1) * Math.pow(26, j);
	    }
	    return result;
	};
`s.charCodeAt(i)`为取得字符串对应字母的ASCII码，`'A'.charCodeAt()`是取得字母A的ASCII，将前者减去后者，就是字母对应的正确权重。
