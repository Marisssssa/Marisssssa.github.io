---
layout: post
title:  "Leetcode0034.searchRange"
date:   2022-01-11
excerpt: "Leetcode在排序数组中查找元素的第一个和最后一个位置."
tag:
- leetcode 
- 算法
comments: false
---

<center><b>0034.searchRange.</b> </center>

# Leetcode题目0034.searchRange

给定一个按照升序排列的整数数组 nums，和一个目标值 target。找出给定目标值在数组中的开始位置和结束位置。

如果数组中不存在目标值 target，返回 [-1, -1]。

进阶：

你可以设计并实现时间复杂度为 O(log n) 的算法解决此问题吗？

| ![34eg1](https://gitee.com/llesssssa/imagebed/raw/master/master/202201231355685.png) | ![34eg3](https://gitee.com/llesssssa/imagebed/raw/master/master/202201231355684.png) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![34eg2](https://gitee.com/llesssssa/imagebed/raw/master/master/202201231355777.png) |                                                              |

解法：利用二分法进行两次遍历确认两个数，两个遍历的边界设定不同以得到不同位置的目标值。

时间复杂度：$O(log(n))$

空间复杂度：$O(1)$

代码：

```c++
#include <iostream>
#include <vector>

using namespace std;

class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
        int len=nums.size();
        if(len==0)
            return {-1,-1};
        if(len==1)
        {
            if(nums.at(0)==target)
                return {0,0};
            else
                return {-1,-1};
        }
        int left=0,right=len-1,mid;
        while(left<right)
        {
            mid=(left+right)/2;
            if(target<=nums.at(mid))
                right=mid;
            else
                left=mid+1;
        }
        if(left>right||nums.at(left)!=target)
            return {-1,-1};
        int l=0,r=len-1,m;
        while(l<r)
        {
            m=(l+r)/2+1;
            if(target<nums.at(m))
                r=m-1;
            else
                l=m;
        }
        if(left>right||l>r)
            return {-1,-1};
        else
            return {left,r};
    }
};

int main()
{
    vector<int> v={1,4};
    int t=4;
    Solution s;
    vector<int> res;
    res=s.searchRange(v,t);
    for (vector<int>::iterator it = res.begin(); it != res.end(); it++)
    {
        cout<<*it<<" ";
    }
    return 0;
}

```



END