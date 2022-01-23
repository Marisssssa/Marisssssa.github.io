---
layout: post
title:  "Leetcode0035.searchInsert"
date:   2022-01-11
excerpt: "Leetcode搜索插入位置."
tag:
- leetcode 
- 算法
comments: false
---

<center><b>0035.searchInsert.</b> </center>

# Leetcode题目0035.searchInsert

给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

请必须使用时间复杂度为 O(log n) 的算法。

| ![35eg1](https://gitee.com/llesssssa/imagebed/raw/master/master/202201231420509.png) | ![35eg2](https://gitee.com/llesssssa/imagebed/raw/master/master/202201231420599.png) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![35eg3](https://gitee.com/llesssssa/imagebed/raw/master/master/202201231421203.png) | ![35eg4](https://gitee.com/llesssssa/imagebed/raw/master/master/202201231421706.png) |

解法：利用二分法进行遍历找到可插入位置。

时间复杂度：$O(log(n))$

空间复杂度：$O(1)$

代码：

```c++
#include <iostream>
#include <vector>

using namespace std;

class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int len=nums.size();
        if(len==0)
            return 0;
        if(target>nums.at(len-1))
            return len;
        int left=0,right=len-1,result=0,mid;
        while(left<=right)
        {
            mid=(left+right)/2;
            if(target<=nums.at(mid))
            {
                result=mid;
                right=mid-1;
            }
            else
                left=mid+1;
        }
        return result;
    }
};

int main()
{
    Solution s;
    vector<int> v={0};
    int n=1,res;
    res=s.searchInsert(v,n);
    cout << res << endl;
    return 0;
}
```



END