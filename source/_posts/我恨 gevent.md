报错了一晚上，最后发现是 python 版本不对。3.11，3.12，3.8，3.10 试了个遍，最后 3.10 终于编译通过了😮‍💨

![python-3.8](https://img2024.cnblogs.com/blog/2778973/202401/2778973-20240119203157802-812092685.jpg)

![python-3.11](https://img2024.cnblogs.com/blog/2778973/202401/2778973-20240119203224800-1834350958.jpg)

![python-3.12](https://img2024.cnblogs.com/blog/2778973/202401/2778973-20240119203230098-1147274050.jpg)

![python-3.10](https://img2024.cnblogs.com/blog/2778973/202401/2778973-20240119203249104-1705708515.jpg)

还有这个 greenlet，每次都是它和 gevent 合着来恶心我这次记录一下，编译成功的版本是 `gevent==21.12.0`（是的，修改 gevent 的版本让 greenlet 编译成功），希望我下次再被折磨的时候能想起来看这个帖子｡°(°¯᷄◠¯᷅°)°｡

> 转载自 [我恨 gevent | 小红书](https://www.xiaohongshu.com/explore/6589f04b000000001c0115ea)