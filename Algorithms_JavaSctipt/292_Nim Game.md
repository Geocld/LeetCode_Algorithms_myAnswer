##292、Nim Game
> You are playing the following Nim Game with your friend: There is a heap of stones on the table, each time one of you take turns to remove 1 to 3 stones. The one who removes the last stone will be the winner. You will take the first turn to remove the stones.<br>
Both of you are very clever and have optimal strategies for the game. Write a function to determine whether you can win the game given the number of stones in the heap.<br>
For example, if there are 4 stones in the heap, then you will never win the game: no matter 1, 2, or 3 stones you remove, the last stone will always be removed by your friend.<br>
Hint:<br>
If there are 5 stones in the heap, could you figure out a way to remove the stones such that you will always be the winner?<br>

石头取胜游戏，你和另一个人玩该游戏，有一堆石头，每人每次按次序取1-3个石头，取到最后一块石头的人获胜，你是第一个开始取石头的人，那么如何在游戏一开始就根据石头的数量直接知道自己是否有胜算。

**分析：**假设你是A，对手为B，从B的角度上看，假如他为了获胜，他只需要在游戏的最后一轮给你剩下4个石头，那么最后一轮，不管你怎么取，你都会剩下一个石头，B就能获得胜利，故只要石头的数量不是4的倍数，那么你就可以取得游戏的胜利。事实上，不管是A还是B，只要在最后一轮给对手剩下4个石头，下一个人都可以取得胜利。故答案为：

	/**
	 * @param {number} n
	 * @return {boolean}
	 */
	var canWinNim = function(n) {
	    if (n % 4 === 0) {
	        return false
	    }
	    return true
	};