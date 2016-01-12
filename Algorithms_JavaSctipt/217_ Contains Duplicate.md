##217. Contains Duplicate

>Given an array of integers, find if the array contains any duplicates. Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct. 

判断数组中是否有超过两次出现的元素。

**分析：**

刚开始看到这题时，我第一反应是通过如下思路求解：

	loop(i = 0; i < n; i ++)
		loop(j = 0; j < n; j++)
		if (arr[i] == arr[j] && i != j)
			return true

这种做法可以得到正确的答案，时间复杂度为O(n^2),而且在leetcode上提交答案时runtime超时了。。。

再思考另一种方式后，得到了通过排序的方法获得答案：如果对一个数组排序，如果出现相同的元素，那么这两个元素必定会靠在一起，即`a[i] == a[i+1]`.

	/**
	 * @param {number[]} nums
	 * @return {boolean}
	 */
	var containsDuplicate = function(nums) {
	    var len = nums.length;
	    nums = nums.sort(function(a,b) {
	       if(a < b) {
	           return -1;
	       }
	       else if(a > b) {
	           return 1;
	       }
	       else {
	           return 0;
	       }
	    });
	    for(var i = 0; i < len; i++) {
	        if (nums[i] === nums[i + 1]) {
	            return true;
	        }
	    }
	    return false;
	};