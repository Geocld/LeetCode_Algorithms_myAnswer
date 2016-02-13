##232. Implement Queue using Stacks
> Implement the following operations of a queue using stacks.

>    push(x) -- Push element x to the back of queue.<br>
>    pop() -- Removes the element from in front of queue.<br>
>    peek() -- Get the front element.<br>
>    empty() -- Return whether the queue is empty.<br>

>Notes:

>    
- You must use only standard operations of a stack -which means only push to top, peek/pop from top, size, and is empty operations are valid.<br>
>    
- Depending on your language, stack may not be supported natively. You may simulate a stack by using a list or deque (double-ended queue), as long as you use only standard operations of a stack.<br>
>- You may assume that all operations are valid (for example, no pop or peek operations will be called on an empty queue).

使用栈实现队列操作。

**分析：**队列是一个先进先出(FIFO)的数据结构。在这篇博客([JavaScript中的数据结构——队列(Queue)](http://geocld.github.io/2015/12/29/queue_in_javascript/))中有完整的介绍说明，这里不在重复，直接上代码：

	/**
	 * @constructor
	 */
	var Queue = function() {
	    this._oldestIndex = 1;
	    this._newestIndex = 1;
	    this._storage = {};
	};
	
	/**
	 * @param {number} x
	 * @returns {void}
	 */
	//队列入队操作
	Queue.prototype.push = function(x) {
	    this._storage[this._newestIndex] = x;
	    this._newestIndex++;
	};
	
	/**
	 * @returns {void}
	 */
	//队列出队操作
	Queue.prototype.pop = function() {
	    var oldestIndex = this._oldestIndex,
	        newestIndex = this._newestIndex,
	        deletedData;
	 	//判断是否存在假溢出、空队列的情况
	    if (oldestIndex !== newestIndex) {
	        deletedData = this._storage[oldestIndex];
	        delete this._storage[oldestIndex];
	        this._oldestIndex++;
	 
	        return deletedData;
	    }
	};
	
	/**
	 * @returns {number}
	 */
	//获得队首元素操作
	Queue.prototype.peek = function() {
	    var font = this._oldestIndex;
	    return this._storage[font];
	};
	
	/**
	 * @returns {boolean}
	 */
	//判断队列是否为空
	Queue.prototype.empty = function() {
	    var oldestIndex = this._oldestIndex,
	        newestIndex = this._newestIndex;
	    return oldestIndex === newestIndex ? true : false;
	};
