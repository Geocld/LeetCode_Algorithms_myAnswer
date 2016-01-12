## 242. Valid Anagram ##
>Given two strings s and t, write a function to determine if t is an anagram of s.

>For example,
s = "anagram", t = "nagaram", return true.
s = "rat", t = "car", return false. 

判断两个string是否为`变位数`.

**分析：**

判断变位数最原始的方法是创建两个string对应的Array，通过两层循环进行逐个判断，最后得到正确结果，计算的时间复杂度为O(n^2)。

为了达到更快效率更高的算法，需要利用变位数的一个特点：变位数的前提条件是string长度相等。故本题的解题思路是：先判断长度是否相等，如相等，进行下一步：对string内的字母进行排序，对比两个string是否相等来达到结果。
（javascript提供了sort()排序方法，不需要使用参数即可对string内的字母进行ASCII排序。）

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