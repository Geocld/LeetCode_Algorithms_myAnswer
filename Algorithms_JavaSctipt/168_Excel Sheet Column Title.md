##168. Excel Sheet Column Title
>Given a positive integer, return its corresponding column title as appear in an Excel sheet.

>For example:
>
	1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 

将十进制数转换为26进制，原理跟`171. Excel Sheet Column Number`完全相反。

**分析：**将十进制转换为非十进制算法主要使用余数定理，例如将4877（10）转成十六进制：

	4877÷16=304....13(D)
	
	304÷16=19....0
	
	19÷16=1....3
	
	1÷16=0....1

这样就计到4877（10）=130D（16）；本题10进制转26进制同理，根据每次计算取得的余数获得相应的字母，再将结果进行拼接：

	/**
	 * @param {number} n
	 * @return {string}
	 */
	var convertToTitle = function(n) {
	    var arr = [];
	    var remain;
	    while(n > 0) {
	        remain = Math.floor((n - 1) % 26);//JavaScript的小数运算需要额外使用Math方法进行处理，使用Math.floor()取得整数部分
	        var mark = String.fromCharCode(65 + remain);
	        arr.push(mark);
	        n = Math.floor((n - 1) / 26);
	    }
	    return arr.reverse().join('');
	};

`String.fromCharCode(65 + remain)`：将数字转换为对应的编码，其中65是字母A的ASCII索引数。