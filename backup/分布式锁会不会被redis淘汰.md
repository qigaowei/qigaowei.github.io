几率很小
无论是LRU还是LFU

FIFO：First In First Out，先进先出，淘汰最早被缓存的对象；
LRU：Least Recently Used，淘汰最长时间未被使用的数据，以时间作为参考；
LFU：Least Frequently Used，淘汰一定时期内被访问次数最少的数据，以次数作为参考；
这些算法在不同层次的缓存上执行时拥有不同的效率和代价，需根据具体场合选择最合适的一种。