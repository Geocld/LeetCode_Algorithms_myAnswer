>Given a non-negative number represented as an array of digits, plus one to the number.

>The digits are stored such that the most significant digit is at the head of the list.

给一个元素是非负整数的数组，给出数组加1后的新数组，需要考虑进位问题。例如：[1,3] + 1 = [1,4],[9] + 1 = [1,0],[9,9] + 1 = [1,0,0].

**分析：**将数组的每一位视为十进制的每一位，需要从数组的最高位开始遍历，同时在遍历的过程中需要考虑当元素为9时加一后的进位，如果元素9不在最高位（对应数组的最低位），则下一位加一返回结果；如果9在最高位，则需要数组的长度加1，数组最低位设置为1，解法如下：

	/**
	 * @param {number[]} digits
	 * @return {number[]}
	 */
	var plusOne = function(digits) {
	    if (digits === null) {
	        return digits;
	    }
	    for (var i = digits.length - 1; i >=0; i--) {
			//如果数组最高位不是9，该位直接加1，退出循环
	        if (digits[i] !== 9) {
	            digits[i]++;
	            break;
	        }
	        else if (digits[i] === 9) {
	            digits[i] = 0;//如果元素为9，将此为设置为0
	            if (i === 0) {
	                digits.splice(0, 0, 1);//如果是数组的最低位为9，那么使用splice()方法在arry[0]处插入1
	            }
	        }
	    }
	    return digits;
	};