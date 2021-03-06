### 407.Trapping-Rain-Water-II

注意此题和一维的版本不一样，无法使用DP的思想。

我们将矩阵所有的边界格子加入一个优先队列，里面的格子按照海拔从低到高排列。这些边界格子相当于闭合的堤岸，围了中间的区域。

我们想象一下海平面逐渐上涨的过程，当海平面cur上涨到优先队列里最矮的那个元素时，就相当于从那里冲破了堤岸，拓展进了内陆、同时会有新的堤岸格子加入队列。如果加入队列的这一系列新格子高度都小于cur，那么它们其实也被淹没了，洪水可以基于它们的位置继续向四周扩展。这个“泛滥”的过程直到队列里面的所有元素高度（也就是首元素）都大于cur为止。在上面的过程中，所有被“淹没”的格子(i,j)，计算```cur-h(i,j)```就是该点的储水量。

然后重复上述的过程，再次想象海平面cur上涨到队列最矮元素的高度，这样就再一次“决堤”，这个泛滥的过程依然是在各地“储水”的机会，直至队列里面的堤岸都高于海平面cur位置，“泛滥”结束。

以上过程中，所有被“决堤”或者被“淹没”的格子，都要做标记，不用重复入队列。直至队列为空停止。



[Leetcode Link](https://leetcode.com/problems/trapping-rain-water-ii)
