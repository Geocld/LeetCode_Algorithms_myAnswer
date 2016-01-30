##242. Valid Anagram
>Given two strings s and t, write a function to determine if t is an anagram of s.

>For example,
>
>s = "anagram", t = "nagaram", return true.
>
>s = "rat", t = "car", return false. 

判断两个字符串是否为变位数。

**分析：**变位数的特征为字符串长度相同，但是字符串中的位置或许不同，我想到的解决方案为：将字符串拆分为数组，然后对其进行排序，再将排序后的数组合并为字符串，如果得到的新字符串相等，则两个字符串是变位数。（注：此方法效率极低，后续会继续更新效率更高的解决方案。）

	/**
	 * @param {string} s
	 * @param {string} t
	 * @return {boolean}
	 */
	var isAnagram = function(s, t) {
	    if(s.length !== t.length) {
	        return false;
	    }
	    var arr1 = s.split(''),
	        arr2 = t.split('');
	    if (arr1.sort().toString() === arr2.sort().toString()) {
	        return true;
	    }
	    else {
	        return false;
	    }
	};