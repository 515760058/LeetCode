# LeetCode算法

## 常用函数整理
### 求和
### 进制转换
### 字符串
- leetcode394 字符串解码

### (二分)查找
### 最大/小值

STL算法常用函数：
排列组合：
next_permutation() 是取出当前范围内的排列，并重新排序为下一个排列，
prev_permutation() 是取出指定范围内的序列并将它重新排序为上一个序列。
如果不存在下一个序列或上一个序列则返回 false，否则返回 true
求和/拼接：
对于数值型的vec，求和：
int sum = accumulate(vec.begin() , vec.end() , 0);
对于string型的vec，拼接：
vector<string> vec{"abc", "def", "ghj"};     
string str = accumulate(vec.begin() , vec.end() , string("xxx"));   //结果是”xxxabcdefghj”

转换transform
transform(S.begin(), S.end(), S.begin(), ::toupper);//小写字母转大写

//删去所有的破折号
for(auto it=S.begin(); it != S.end(); ++it)
    if(*it == '-'){
        S.erase(it);
        --it;
  }
}

//最大值 最小值的迭代器
Auto iter  = min_element(houses.begin(), houses.end());
Auto iter  = max_element(houses.begin(), houses.end());
通过解引用迭代器，就可以获得最值。


二分查找 

https://www.jianshu.com/p/cb0d5488bb6a

https://blog.csdn.net/qian2213762498/article/details/79250097

lower_bound ：返回一个非递减序列[first, last)中的第一个大于等于值val的位置（迭代器）

upper_bound：返回一个非递减序列[first, last)中的第一个大于值val的位置（迭代器）


binary_search(beg,end,val)： 以二分法检索的方式在[beg,end）之间查找val，找到返回true，找不到返回false。
equal_range(beg,end,val)：返回一个迭代器对(i,j)，其中i是在不破坏次序的前提下，value可插入的第一个位置（>=亦即lower_bound），j则是在不破坏次序的前提下，value可插入的最后一个位置（>亦即upper_bound）因此，[i,j)内的每个元素都等同于value，而且[i,j)是[beg,end)之中符合此一性质的最大子区间


字符串 <==> 数字
123 = atoi(“123”)   
“123” = to_string(123)

进制转换

#include<cstdio>
#include<cstdlib> 
strtol 函数：将一个任意1-36进制数转化为10进制数，返回是long int型。
 函数为long int strtol(const char *nptr, char **endptr, int base)
 base是要转化的数的进制，非法字符会赋值给endptr，nptr是要转化的字符，例如：
char buffer[20]="10379cend$3";  //8进制
char *stop;
Long int num = strtol(buffer, &stop, 8));   //10进制结果num=543  stop=”9cend$3” 

itoa()函数：将一个10进制数转换为任意的2-36进制字符串
函数原型：char*  itoa(int value, char*string, int radix);
例如：itoa(num, str, 2); num是一个int型的，是要转化的10进制数，str是转化结果，后面的值为目标进制。

Vector
//放入/移除： Push_back(xx)   pop_back()
//第一个/最后一个元素   front()    back()
//删除（区间）  Erase(iter)    erase(begin, end)    包括begin不含end：[begin, end)
clear();   //清空vec的所有元素
empty(); //判断a是否为空，空则返回true，非空则返回false

#include<algorithm>
sort(a.begin(), a.end(), cmp);  //排序
reverse(a.begin(), a.end());   //倒置
Int idx = find(a.begin(), a.end(), value) - a.begin();   //查找value的下标

二维数组
Vector<vector<int>>  num(row, vector<int>(col, value)); //row行col列 初始值value

结构体：
struct A {
	int id;
Int age;
	string name;
 	//重载小于运算符，可以创建set<A> s;
	bool operator<(const A &b) const {
If(id== b.id){//根据id去重
Return false; 
}
		return age < b.age;//按年龄排序
	}
};

- 面试题 16.11. 跳水板  简单 数组


## 并查集
### 相关链接
1, https://blog.csdn.net/qq_35546304/article/details/51879063

2, https://blog.csdn.net/Guo15331092/article/details/78702686

3, https://blog.csdn.net/Guo15331092/article/details/78785910

4, https://blog.csdn.net/weixin_34101229/article/details/88916917

5, 扩展 https://blog.csdn.net/qq_43256272/article/details/94968647

### 典型题目
- Longest Consecutive Sequence

- 朋友圈 Friend Circles

- Couples Holding Hands

- 冗余连接 Redundant Connection

- 冗余连接2 Redundant Connection II

- Number of Islands

- Accounts Merge 账户合并

- Surrounded Regions
- 面试题 17.07. 婴儿名字
- leetcode785. 判断二分图
- leetcode947. 移除最多的同行或同列石头
- leetcode785. 判断二分图(BFS染色 并查集)



## 单调栈
详细易懂的讲解单调栈 https://leetcode-cn.com/problems/daily-temperatures/solution/javadan-diao-zhan-ni-xu-bian-li-by-hyh-2/
### 相关链接
1, https://www.cnblogs.com/Atanisi/p/7563178.html

2, https://blog.csdn.net/qq_17550379/article/details/86519771

3, https://www.cnblogs.com/1024th/p/10778050.html

4, https://blog.csdn.net/qq_40028201/article/details/89473889

### 典型题目
- 739每日温度
- https://blog.csdn.net/qq_17550379/article/details/86519771

## 回溯法
回溯算法实际上一个类似枚举的搜索尝试过程，主要是在搜索尝试过程中寻找问题的解，当发现已不满足求解条件时，就 “回溯” 返回，尝试别的路径。回溯法是一种选优搜索法，按选优条件向前搜索，以达到目标。但当探索到某一步时，发现原先选择并不优或达不到目标，就退回一步重新选择，这种走不通就退回再走的技术为回溯法，而满足回溯条件的某个状态的点称为 “回溯点”。许多复杂的，规模较大的问题都可以使用回溯法，有“通用解题方法”的美称。

回溯算法的基本思想是：从一条路往前走，能进则进，不能进则退回来，换一条路再试。

### 典型题目
- 17电话号码的字母组合

- 93复原IP地址

- 括号生成

- 组合总和   组合总和II  组合总和III

- 全排列   全排列II   第k个排列

- 子集   子集II

- 单词搜索
- leetcode79 单词搜索
- 剑指 Offer 12 矩阵中的路径
- leetcode698 划分为k个相等的子集 (leetcode473 火柴拼正方形)

- 127单词接龙    单词接龙II    433最小基因变化

## 排序
- C++的写法：

```C++
    #include <algorithm>
    std::sort(a.begin(), a.end());   //默认std::less<int>(), 从小到大
    std::sort(a.begin(), a.end(), std::greater<int>());   //从大到小  #include <functional>
```


- 结构体/类的比较函数的一般写法：
1, 在结构体的内部实现：

```C++
    struct Person {
        string name;
        int age;
        bool operator < (const Person& p) const { //重载小于运算符
            return age < p.age;
        }
    }
```


2, 在外部实现：

```C++
    bool less(const Person& p1, const Person& p2) {
        return p1.age < p2.age;
    }
```
### 典型题目
- 976最大周长三角形
- 524通过删除字母匹配到字典里最长单词
- 75颜色分类
- 767重构字符串
- 853车队
- 969煎饼排序

## 拓扑排序
DAG，有向无环图，可以求拓扑排序，关键路径
### 相关链接
1, https://blog.csdn.net/qq_38984851/article/details/82844186

2, https://www.jianshu.com/p/3347f54a3187

3, https://blog.csdn.net/qq_41713256/article/details/80805338

4, https://www.cnblogs.com/bigsai/p/11489260.html

### 典型题目
-  LeetCode207课程表(判断图中是否存在环)
-  LeetCode210课程表II (求出一种拓扑排序的序列)
- -leetcode802 找到最终的安全状态

## 图算法
- leetcode787 K站中转内最便宜的航班(Bellman-Ford算法)
- leetccode743 网络延迟时间(Dijkstra最短路径)
- leetcode332. 重新安排行程(图的欧拉回路)


## 前缀和
### 相关链接

### 典型题目
- LeetCode560 和为K的子数组
- LeetCode974 和可被 K 整除的子数组
- leetcode554 砖墙

## 字典树
### 相关链接

### 典型题目
- LeetCode_208_Implement_Trie_(Prefix_Tree) 实现Trie(前缀树)
- 211_Add_and_Search_Word--Data_structure_design 添加与搜索单词 - 数据结构设计
- LeetCode 421数组中两个数的最大异或值
- leetcode648 单词替换
- leetcode677 键值映射
- leetcode720 词典中最长的单词
- leetcode面试题17.17多次搜索
- leetcode676 实现一个魔法字典

## 二叉搜索树 BST
### 相关链接

### 典型题目
- leetcode98 验证二叉搜索树
- 面试题04.05. 合法二叉搜索树
- leetcode700 二叉搜索树中的搜索
- leetcode 将有序数组转换为二叉搜索树
- leetcode1382 将二叉搜索树变平衡（重建BST）
- 面试题 04.02. 最小高度树(重建BST)
- leetcode1008. 先序遍历构造二叉树(重建BST)
- leetcode1038 从二叉搜索树到更大和树
- leetcode1373 二叉搜索子树的最大键值和
- 剑指 Offer 54 二叉搜索树的第k大节点
- 剑指 Offer 68 - I. 二叉搜索树的最近公共祖先
- 剑指 Offer 68 - II. 二叉树的最近公共祖先
- 面试题 04.08. 首个共同祖先(非BST)
- leetcode1379. 找出克隆二叉树中的相同节点
- leetcode173 二叉搜索树迭代器
- LeetCode938. 二叉搜索树的范围和
- 面试题 04.06. 后继者


## 树 二叉树 N叉树
### 相关链接
### 典型题目
- 前中后序遍历
- leetcode589 N叉树的前序遍历
- leetcode590 N叉树的后序遍历

- 树的深度
- leetcode559. N叉树的最大深度

- 检验树的性质
- leetcode110 平衡二叉树
- 面试题 04.04. 检查平衡性
- 剑指 Offer 55 - II. 平衡二叉树
- leetcode958 检验完全二叉树

- 层序遍历及其衍生题目
- leetcode 102 二叉树的层序遍历
- leetcode 107 二叉树的层次遍历 II
- 剑指 Offer 32 - I. 从上到下打印二叉树
- 剑指 Offer 32 - II. 从上到下打印二叉树 II
- 剑指 Offer 32 - III. 从上到下打印二叉树 III
- leetcode513. 找树左下角的值
- leetcode1302. 层数最深叶子节点的和
- leetcode 199 二叉树的右视图
- leetcode 在每个树行中找最大值
- leetcode 二叉树的层平均值
- leetcode 二叉树的垂序遍历
- 面试题 04.03. 特定深度节点链表
- LeetCode429. N叉树的层序遍历
- leetcode 117. 填充每个节点的下一个右侧节点指针II


- 重建二叉树
- leetcode654 最大二叉树
- 剑指 Offer 07. 重建二叉树
- leetcode106 从中序与后序遍历序列构造二叉树

- leetcode998. 最大二叉树 II

- 翻转/镜像二叉树
- 剑指 Offer 27. 二叉树的镜像
- leetcode951. 翻转等价二叉树

- 序列化
- leetcode297. 二叉树的序列化与反序列化
- 剑指 Offer 37. 序列化二叉树

- 双层遍历
- leetcode437 路径总和III
- 面试题 04.12. 求和路径
- leetcode1367 二叉树中的列表
- 剑指 Offer 26. 树的子结构
- 面试题 04.10. 检查子树
- leetcode

- 树转图
- leetcode863. 二叉树中所有距离为K的结点
- leetcode1466. 重新规划路线


- 根到叶子的路径
- leetcode1022. 从根到叶的二进制数之和
- leetcode1530. 好叶子节点对的数量
- leetcode1457. 二叉树中的伪回文路径
- leetcode1026. 节点与其祖先之间的最大差值
- leetcode988. 从叶结点开始的最小字符串
- leetcode1448. 统计二叉树中好节点的数目
- 剑指Offer 34. 二叉树中和为某一值的路径


- 删除二叉树节点
- leetcode1325. 删除给定值的叶子节点
- leetcode1110. 删点成林
- leetcode1080 根到叶路径上的不足节点

- 其他
- leetcode1315 祖父节点值为偶数的节点和
- leetcode1104 (之字形)二叉树寻路
- leetcode1372. 二叉树中的最长交错路径(后序遍历)
- leetcode897 递增顺序查找树(二叉树变链表)
- 剑指Offer 28. 对称的二叉树
- leetcode404. 左叶子之和
- leetcode1443. 收集树上所有苹果的最少时间
- leetcode1145. 二叉树着色游戏
- leetcode919 完全二叉树插入器
- leetcode1339 分裂二叉树的最大乘积(后序遍历)
- leetcode979. 在二叉树中分配硬币(后序遍历)
- leetcode1261. 在受污染的二叉树中查找元素
- leetcode993. 二叉树的堂兄弟节点
- leetcode965. 单值二叉树
- leetcode116. 填充每个节点的下一个右侧节点指针
- leetcode968. 监控二叉树
- leetcode872 叶子相似的树
- leetcode430 扁平化多级双向链表
- leetcode1376 通知所有员工所需的时间

## 树状数组 线段树
### 相关链接
- 树状数组
- https://blog.csdn.net/Small_Orange_glory/article/details/81290634
- https://blog.csdn.net/zcz5566719/article/details/107185515
- https://blog.csdn.net/Mo_1034923393/article/details/107675374
- 线段树
- https://blog.csdn.net/zearot/article/details/52280189
- https://blog.csdn.net/anlian523/article/details/80766794

### 典型题目
- leetcode307 区域和检索-数组可修改 (单点修改 区间计数)  树状数组
- leetcode493 翻转对
- leetcode315 计算右侧小于当前元素个数
- leetcode327 区间和的个数
- leetcode1109 航班预订统计 (区间修改 单间计数) 公交车算法

## 区间
### 典型题目
- leetcode986 区间列表的交集
- leetcode56 合并区间(区间的并集)
- leetcode228 汇总区间
- leetcode1353 最多可以参加的会议数目
- leetcode1523 在区间范围内统计奇数数目


## 随机数rand()
### 相关链接

### 典型题目
- leetcode 470 用Rand7()实现Rand10()
- leetcode 528 按权重随机选择
- leetcode 478 在圆内随机生成点
- leetcode 497 非重叠矩形中的随机点
- leetcode 519 随机翻转矩阵
- leetcode 710 黑名单中的随机数

## 字符串
字符串输入流  字符串输出流
### 典型题目
- leetcode1023 驼峰式匹配 中等 字符串匹配
- leetcode151 翻转字符串里的单词
- LeetCode468 验证IP地址

## 双指针 三指针
### 相关链接
### 典型题目
- leetcode93 复原IP地址

## 扫描线
### 相关链接
### 典型题目

## 蓄水池采样
### 相关链接
- https://blog.csdn.net/huagong_adu/article/details/7619665
- https://www.jianshu.com/p/7a9ea6ece2af
### 典型题目
- leetcode398. 随机数索引
- leetcode382. 链表随机节点

## 动态规划dp
### 相关链接
### 典型题目
- 面试题17.13. 恢复空格
- leetcode198 打家劫舍
- leetcode213 打家劫舍II
- leetcode337 打家劫舍 III



## 记忆化搜索
### 相关链接
### 典型题目
- POJ1088-滑雪
- leetcode851 喧闹和富有
- leetcode329. 矩阵中的最长递增路径


## 广度优先搜索BFS
### 相关链接
### 典型题目
- leetcode 994 腐烂的橘子(地图分析)
- leetcode1162. 地图分析(腐烂的橘子)
- leetcode934. 最短的桥 dfs+bfs
- leetcode1306. 跳跃游戏 III
- leetcode909 蛇梯棋
- leetcode310. 最小高度树
- leetcode785. 判断二分图(BFS染色 并查集)
- leetcode886 可能的二分法(BFS染色)
- leetcode1091. 二进制矩阵中的最短路径(bfs最短路径的长度)
- leetcode752 打开转盘锁(bfs最短路径的长度)
- leetcode127 单词接龙(bfs最短路径的长度)
- 面试题17.22. 单词转换(bfs最短路径)
- leetcode133. 克隆图
- leetcode1311 获取你好友已观看的视频
- leetcode1129 颜色交替的最短路径
- leetcode690 员工的重要性
- leetcode1466 重新规划路线


## 深度优先搜索DFS
### 相关链接
### 典型题目
- leetcode 200岛屿数量
- leetcode417. 太平洋大西洋水流问题
- leetcode130. 被围绕的区域
- leetcode529. 扫雷游戏
- leetcode1391 检查网格中是否存在有效路径
- 面试题16.19. 水域大小
- leetcode1020. 飞地的数量
- leetcode1034 边框着色
- leetcode1254 统计封闭岛屿的数目
- 面试题 08.10 颜色填充
- leetcode959 由斜杠划分区域

## 优先队列
### 相关链接
### 典型题目
- leetcode 215 数组中的第K个最大元素


## 脑筋急转弯 / 数学
### 相关链接
### 典型题目
- leetcode 1033 移动石子直到连续
- leetcode 1503 所有蚂蚁掉下来前的最后一刻
- leetcode 292 Nim游戏
- leetcode 1227 机座位分配概率
- leetcode 319 灯泡开关
- leetcode 777 在LR字符串中交换相
- leetcode 279 完全平方数
- leetcode 679 24 点游戏
