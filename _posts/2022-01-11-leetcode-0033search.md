---
layout: post
title:  "Leetcode0033.search"
date:   2022-01-11
excerpt: "Leetcode搜索旋转排序数组."
tag:
- leetcode 
- 算法
comments: false
---

<center><b>0033.search.</b> </center>

# Leetcode题目0033.search

整数数组 nums 按升序排列，数组中的值 互不相同 。

在传递给函数之前，nums 在预先未知的某个下标 k（0 <= k < nums.length）上进行了 旋转，使数组变为 [nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]（下标 从 0 开始 计数）。例如， [0,1,2,4,5,6,7] 在下标 3 处经旋转后可能变为 [4,5,6,7,0,1,2] 。

给你 旋转后 的数组 nums 和一个整数 target ，如果 nums 中存在这个目标值 target ，则返回它的下标，否则返回 -1 。

| ![33eg1](https://gitee.com/llesssssa/imagebed/raw/master/master/202201231347002.png) | ![33eg2](https://gitee.com/llesssssa/imagebed/raw/master/master/202201231347695.png) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![33eg3](https://gitee.com/llesssssa/imagebed/raw/master/master/202201231347960.png) |                                                              |

解法：利用二分法进行遍历。

时间复杂度：$O(log(n))$

空间复杂度：$O(1)$

代码：

```c++
#include <iostream>
#include <vector>

using namespace std;

class Solution {
public:
    int search(vector<int>& nums, int target) {
        if(nums.size()==0)
            return -1;
        if(nums.size()==1)
        {
            if(nums.at(0)==target)
                return 0;
            else
                return -1;
        }
        int left=0,right=nums.size()-1;
        int mid;
        while(left<=right)
        {
            mid=(left+right)/2;
            if(target==nums.at(mid))
                return mid;
            if(nums.at(0)<=nums.at(mid))
            {
                if(target>=nums.at(0)&&target<nums.at(mid))
                {
                    right=mid-1;
                }
                else
                    left=mid+1;
            }
            else
            {
                if(target>nums.at(mid)&&target<=nums.at(right))
                {
                    left=mid+1;
                }
                else
                    right=mid-1;
            }
        }
        return -1;
    }
};

int main()
{
    vector<int> v={6,7,0,1,2,4,5};
    Solution s;
    int res,t=0;
    res=s.search(v,t);
    cout << res << endl;
    return 0;
}
```



END