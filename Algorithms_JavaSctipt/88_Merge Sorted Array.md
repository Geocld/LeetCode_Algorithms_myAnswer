##88. Merge Sorted Array
>Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

>Note:
>
You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2. The number of elements initialized in nums1 and nums2 are m and n respectively.

合并两个有序数组，使得最后得到的数组也是有序的。假设nums1有m个数，nums2有n个数，并且nums1后有足够的空间存放nums2的元素个数，将结果保存在nums1中。

**分析：**此题最原始的解法是将两个数组合并，然后再重新排序，最后得到有序的数组，这种做法的时间复杂度为O（nlogn），但是这样没有用到数组有序的条件。

另一种做法是从数组的开头进行遍历，比较较小的数再放入到数组中，但这样就需要数组插入操作，不合理。

最后一种思路是从数组最后合并，因为nums1后面有足够的空间，因此每次比较出最大的数放在数组nums1的倒数第一个空位即可。

	/**
	 * @param {number[]} nums1
	 * @param {number} m
	 * @param {number[]} nums2
	 * @param {number} n
	 * @return {void} Do not return anything, modify nums1 in-place instead.
	 */
	var merge = function(nums1, m, nums2, n) {
	    var new_pos = m + n - 1;
	    var pos1 = m - 1;
	    var pos2 = n - 1;
	    while(pos1 >= 0 && pos2 >= 0) {
	        if (nums1[pos1] < nums2[pos2]) {
	            nums1[new_pos--] = nums2[pos2--];
	        }
	        else {
	            nums1[new_pos--] = nums1[pos1--];
	        }
	    }
	    while(pos2 >=0) {
	        nums1[new_pos--] = nums2[pos2--]
	    }
	};