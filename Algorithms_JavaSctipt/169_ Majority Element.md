##169. Majority Element
>Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

>You may assume that the array is non-empty and the majority element always exist in the array.

给出一个长度为n的数组，找出重复次数≥`n/2`的元素（假设符合情况的元素都存在）。

**分析：**如果本题思路是一个个去记录数组元素的出现次数，那会十分复杂，使用的额外的空间也很大（至少需要额外添加一个辅助数组），本题的关键在于重复出现≥`n/2`，如果数组是有序数组，那个这个重复出现的元素必定会在数组中间，即`arr[middle]`.

	/**
	 * @param {number[]} nums
	 * @return {number}
	 */
	var majorityElement = function(nums) {
	    var len = nums.length;
	    var a;
	    if (len === 1) {
	        return nums[0];
	    }
	    nums.sort();//对数组进行排序，此处排序直接使用javascript的排序方法即可(将相同元素凑在一起)
	    a = Math.floor(len / 2);
	    return nums[a];
	};