##26. Remove Duplicates from Sorted Array
> Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.

>Do not allocate extra space for another array, you must do this in place with constant memory.

>For example,
Given input array nums = [1,1,2],

>Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively. It doesn't matter what you leave beyond the new length. 

移除有序数组中的重复项。

**分析：**本题只要求返回剔除重复元素后数组的长度，原数组的重复元素并没有删除，我这里使用的方法是使用数组的splice(),将重复元素剔除后返回新数组：

	/**
	 * @param {number[]} nums
	 * @return {number}
	 */
	var removeDuplicates = function(nums) {
	    for (var i = 0; i < nums.length; i++) {
			//因数组是已排序好的，所以针对存在重复的元素，存在nums[i] === nums[i + 1]的特性
	        if (nums[i] === nums[i + 1]) {
	            nums.splice(i, 1);
	            i = i - 1;
	        }
	    }
	    return nums.length;
	};