# LeetCode算法

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
1, 在外部实现：

```C++
    bool less(const A& a1, const A& a2) {
        return a1 < a2;
    }
```

2, 在结构体的内部实现：

```C++
    struct Person {
        string name;
        int age;
        bool operator < (const Person& p) const { //重载小于运算符
            return age < p.age;
        }
    }
```

### 典型题目
- 976最大周长三角形
- 524通过删除字母匹配到字典里最长单词
- 75颜色分类
- 767重构字符串
- 853车队
- 969煎饼排序



