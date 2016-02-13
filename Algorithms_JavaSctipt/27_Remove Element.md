##27. Remove Element
>Given an array and a value, remove all instances of that value in place and return the new length. 

>The order of elements can be changed. It doesn't matter what you leave beyond the new length. 

给一个数组，将指定元素删除，并返回新长度。(新长度之后的元素可以无视)

**分析:**由于此题不要求返回删除指定元素后的新数组，且可以无视数组新长度之后的元素，故可以直接使用元素位移来将指定元素删除。

	/**
	 * @param {number[]} nums
	 * @param {number} val
	 * @return {number}
	 */
	var removeElement = function(nums, val) {
	    var index = 0;
	    for (var i = 0; i < nums.length; i++) {
	        if (nums[i] !== val) {
	            nums[index++] = nums[i];
	        }
	    }
	    return index;
	};