##225. Implement Stack using Queues
>Implement the following operations of a stack using queues.

>- push(x) -- Push element x onto stack.
>- pop() -- Removes the element on top of the stack.
>- top() -- Get the top element.
>- empty() -- Return whether the stack is empty.

>Notes:
>
>- You must use only standard operations of a queue -- which means only push to back, peek/pop from front, size, and is empty operations are valid.
- Depending on your language, queue may not be supported natively. You may simulate a queue by using a list or deque (double-ended queue), as long as you use only standard operations of a queue.
- You may assume that all operations are valid (for example, no pop or top operations will be called on an empty stack).

使用队列实现栈操作。

**分析：**由于JavaScript内置没有队列的数据结构，故只使用JavaScript实现栈操作，具体可以参考[JavaScript中的数据结构——栈(Stack)](http://geocld.github.io/2015/12/28/stack_in_javascript/)。

	/**
	 * @constructor
	 */
	var Stack = function() {
	    this._size = 0;
	    this._storage = {};
	};
	
	/**
	 * @param {number} x
	 * @returns {void}
	 */
	//入栈操作
	Stack.prototype.push = function(x) {
	    // 增加数据长度
	    var size = this._size++;
	 
	    // 将数据加到栈的顶部
	    this._storage[size] = x;
	};
	
	/**
	 * @returns {void}
	 */
	//出栈操作
	Stack.prototype.pop = function() {
	    var size = this._size,
	        deletedData;
	    if(size) {
	        deletedData = this._storage[size];
	     
	        delete this._storage[size];
	        this._size--;
	      }
	};
	
	/**
	 * @returns {number}
	 */
	//获取栈顶元素
	Stack.prototype.top = function() {
	    return this._storage[this._size - 1];
	};
	
	/**
	 * @returns {boolean}
	 */
	//判断是否为空栈
	Stack.prototype.empty = function() {
	    return this._size === 0 ? true : false;
	};

