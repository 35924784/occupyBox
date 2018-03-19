# occupyBox
个人上线项目开源

## 这是我的个人上线项目，17.5.18上线app store [occupyBox](https://itunes.apple.com/cn/app/occupybox/id1228559683?l=en&mt=8)
## 游戏规则：
每个box都有两个状态，即free状态（数据源为NO）以及 occupied状态（数据源为YES） 初始状态都为free状态

当box被点击，那么该box的当前状态会变为对立状态，即free->occupied 或者 occupied->free

同时该box相邻（不包含对角线相邻的box）的box状态也会互换

当所有的box都变为occupied状态时游戏结束
<br>
如图可以看到，游戏规则其实很简单：
将所有的方块都变色即为胜利✌️，之前做的时候并没有计算不同阶数的可用性。最高玩到6阶36步走完
<br>
![image](http://occmuwiio.bkt.clouddn.com/IMG_1391.PNG)
<br>
思路：

根据被点击box的索引规则区分 设阶数为:d

### 1：边角索引规律

     左上：x0 = 0

     相邻：

                 x0 + 1

                 x0 + d

     右上：x1 = 阶数 - 1

     相邻：

                  x1 - 1

                  x1 + d

      左下：x2 = 阶数的平方 - 阶数

      相邻：

                   x2 - d

                   x2 + 1

      右下：x3 = 阶数的平方 - 1

      相邻：

                    x3 - 1

                    x3 - d

### 2：边线索引规律（不包括边角） [y0]表示索引集合 [y0] + 1表示y0中每个索引都 + 1得到新索引

       top：

                   x0 < [y0] < x1

       相邻：

                    [y0] + d

                    y0 - 1 >= 0

                    y0 + 1 <= x1

        left：

                     [y1] = d的整数倍(0 < 倍数 < d) 例如四阶左边线索引[y1] =        [4,8]

        相邻：

                     [y1] + 1

                     y2 - d >= 0

                     y2 + d <= x2

         bottom：

                     x2 < [y2] < x3

         相邻：

                     [y2] - d

                     y2 - 1 >= x2

                     y2 + 1 <= x3

         right：

                     [y3] = [y1] + (d - 1)

### 3：其他 z

         相邻：

                     z - d

                     z - 1

                     z + d

                     z + 1
                     
<br>                   
<br>
如图可以看到，游戏规则其实很简单：<br>
将所有的方块都变色即为胜利✌️，之前做的时候并没有计算不同阶数的可用性。最高玩到6阶36步走完
<br>
![image](http://occmuwiio.bkt.clouddn.com/IMG_1391.PNG)
<br>
### 现在将这个小游戏源码放出来纯属共勉需求，共同学习。
我也希望更多的个人项目能够开源，毕竟不管好与不好，其中都有值得学习的地方。

