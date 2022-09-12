---
layout: post
title:  "Leetcode0011.maxArea"
date:   2022-01-08
excerpt: "Leetcode盛最多水的容器."
tag:
- leetcode 
- 算法
comments: false
---

<center><b>0011.maxArea.</b> </center>

# Leetcode题目0011.maxArea

题目：盛最多水的容器

给你 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0) 。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。说明：你不能倾斜容器。

| ![11eg1](https://gitee.com/llesssssa/imagebed/raw/master/master/202201081347609.png) | ![11eg2](https://gitee.com/llesssssa/imagebed/raw/master/master/202201081347009.png) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![11eg3](https://gitee.com/llesssssa/imagebed/raw/master/master/202201081347836.png) | ![11eg4](https://gitee.com/llesssssa/imagebed/raw/master/master/202201081348672.png) |

1.暴力解法：

未通过，时间超出限制。

时间复杂度：$O(n^2)$

```c++
#include <iostream>
#include <vector>
#include <algorithm>
#include <cmath>

using namespace std;

class Solution {
public:
    int maxArea(vector<int>& height) {
        int result=0,area;
        for(int i=0;i<(int)height.size();i++)
        {
            for(int j=i+1;j<(int)height.size();j++)
            {
                area=min(height.at(i),height.at(j))*abs(i-j);
                result=max(area,result);
            }
        }
        return result;
    }
};

int main()
{
    int res;
    Solution s;
    vector<int> v={1,8,6,2,5,4,8,3,7};
    res=s.maxArea(v);
    cout <<res<< endl;
    return 0;
}
```

2.利用两个指针，分别从数据的头和尾开始，循环计算面积并记录较大值，其中过程中两个指针所指的值哪个小哪个就往另一方向挪一。

时间复杂度：$O(n)$

空间复杂度：$O(1)$

代码：

```c++
#include <iostream>
#include <vector>
#include <algorithm>
#include <cmath>

using namespace std;

class Solution {
public:
    int maxArea(vector<int>& height) {
        int result=0,area;
        for(int i=0;i<(int)height.size();i++)
        {
            for(int j=i+1;j<(int)height.size();j++)
            {
                area=min(height.at(i),height.at(j))*abs(i-j);
                result=max(area,result);
            }
        }
        return result;
    }
};

int main()
{
    int res;
    Solution s;
    vector<int> v={1,8,6,2,5,4,8,3,7};
    res=s.maxArea(v);
    cout <<res<< endl;
    return 0;
}
```



END