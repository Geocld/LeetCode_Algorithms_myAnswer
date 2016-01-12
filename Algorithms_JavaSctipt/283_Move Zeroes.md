##283. Move Zeroes
> Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.
> 
For example, given `nums = [0, 1, 0, 3, 12]`, after calling your function, nums should be `[1, 3, 12, 0, 0]`. 

> Note:

>1.You must do this in-place without making a copy of the array.
2.Minimize the total number of operations.

给一个数字数组，将数组中的所有0移动到数组末端。

要求：

1.移动需要在原数组中进行，不需要辅助数组。

2.操作最小化（我的理解是时间复杂度最低）

**分析：**

1.此题最原始的方法是准备一个辅助数组，将非零数保存到复制数组中，同时记录零的个数，最后再将零加到辅助数组的最后，但这样需要额外的存储空间。

2.在原数组中进行数值操作，对数组进行遍历，如遍历到的位置不为零，那么后一位元素提前，在最后一个键值后统一补上`0`，时间复杂度O(n)。

	/**
	 * @param {number[]} nums
	 * @return {void} Do not return anything, modify nums in-place instead.
	 */
	var moveZeroes = function(nums) {
	    var count = 0;
	    if (nums.length === 0) {
	        return
	    }
	    else {
	        for (var i = 0; i < nums.length; i++) {
	            if (nums[i] !== 0) {
	                nums[count++] = nums[i];
	            }
	        }
	        
	        for (var i = count; i < nums.length; i++) {
	            nums[i] = 0;
	        }
	    }
	};