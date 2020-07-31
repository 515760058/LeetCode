# LeetCode算法

## 常用函数整理
### 求和
### 进制转换
### 字符串
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
Auto iter  = max_element(houses.begin(), houses.end());
二分查找
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
- leetcode1382 将二叉搜索树变平衡
- leetcode1038. 从二叉搜索树到更大和树

## 树状数组 线段树
### 相关链接

### 典型题目
- leetcode307 区域和检索-数组可修改  树状数组

## 随机数rand()
### 相关链接

### 典型题目
- leetcode 470 用Rand7()实现Rand10()
- leetcode 528 按权重随机选择
- leetcode 478 在圆内随机生成点
- leetcode 497 非重叠矩形中的随机点
- leetcode 519 随机翻转矩阵


## 字符串
字符串输入流  字符串输出流
### 典型题目
- leetcode1023 驼峰式匹配 中等 字符串匹配





