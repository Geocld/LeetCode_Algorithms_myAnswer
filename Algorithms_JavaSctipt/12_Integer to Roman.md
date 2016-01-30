##12. Integer to Roman
>Given an integer, convert it to a roman numeral.

>Input is guaranteed to be within the range from 1 to 3999.

将阿拉伯数字转换为罗马数字。

**分析：**根据罗马数字的规律，将下表数字枚举在二维数组中，分别取千位、百位、十位和个位的数字，找到对应的罗马数字组合成字符串。（注：罗马数字没有0）
![](http://i.imgur.com/GfAEiLg.jpg)

	/**
	 * @param {number} num
	 * @return {string}
	 */
	var intToRoman = function(num) {
	    var arr = [
	        ['','I','II','III','IV','V','VI','VII','VIII','IX'],
	        ['','X','XX','XXX','XL','L','LX','LXX','LXXX','XC'],
	        ['','C','CC','CCC','CD','D','DC','DCC','DCCC','CM'],
	        ['','M','MM','MMM','','','','','',''],
	    ];
	    var s = '';
	    s += arr[3][Math.floor((num / 1000) % 10)] + arr[2][Math.floor((num / 100) % 10)] + arr[1][Math.floor((num / 10) % 10)] + arr[0][Math.floor(num % 10)];
	    return s;
	};