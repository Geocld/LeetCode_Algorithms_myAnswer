##9. Palindrome Number
>Determine whether an integer is a palindrome. Do this without extra space.

判断一个整数是否是回文数，要求不需要额外的计算空间。

**分析：**回文数即将原数反转后跟原数一致，故本题的解法有两种：

1. 将整数拆分为数组，然后将数组反转，再和原数组比较，如果二者相等，则给出的整数是回文数，但是本题还要多考虑负数的情况，数组反转时需要注意不要将负数符号反转；
2. 将原整数提取各位然后生成反转后的整数，这样的做法是可以保留整数的符号，下面将采用这种做法：


		/**
		 * @param {number} x
		 * @return {boolean}
		 */
		var isPalindrome = function(x) {
		    var rev = 0, a = x;
			//分别提取原数x的个、十、百、千位进行反转组合，保留原数符号
		    while(x > 0) {
		        rev = rev * 10 + x % 10;
		        x = Math.floor(x / 10);
		    }
		    return rev === a ? true : false;
		};