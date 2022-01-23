---
layout: post
title:  "Leetcode0031.nextPermutation"
date:   2022-01-11
excerpt: "Leetcode下一个排列."
tag:
- leetcode 
- 算法
comments: false
---

<center><b>0031.nextPermutation.</b> </center>

# Leetcode题目0031.nextPermutation

实现获取 下一个排列 的函数，算法需要将给定数字序列重新排列成字典序中下一个更大的排列（即，组合出下一个更大的整数）。

如果不存在下一个更大的排列，则将数字重新排列成最小的排列（即升序排列）。

必须 原地 修改，只允许使用额外常数空间。

| ![31eg1](https://gitee.com/llesssssa/imagebed/raw/master/master/202201231322001.png) | ![31eg2](https://gitee.com/llesssssa/imagebed/raw/master/master/202201231322162.png) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![31eg3](https://gitee.com/llesssssa/imagebed/raw/master/master/202201231322296.png) | ![31eg4](https://gitee.com/llesssssa/imagebed/raw/master/master/202201231322394.png) |

解法：从后面开始遍历找到当前值a比当前值的后一个小，再用另一个指针从最后面开始遍历a之后的部分寻找比a大的第一个值b，将a与b调换，再将调换后的b值所在位置后的所有数颠倒。

时间复杂度：$O(n)$

空间复杂度：$O(1)$

代码：

```c++
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

class Solution {
public:
    vector<int> nextPermutation(vector<int>& nums) {
        int left=nums.size()-2,right=nums.size()-1;
        for(left;left>=0;left--)
        {
            if(nums.at(left)<nums.at(left+1))
            {
                break;
            }
        }
        if(left>=0)
        {
            for(right;right>left;right--)
            {
                if(nums.at(right)>nums.at(left))
                {
                    break;
                }
            }
            swap(nums.at(left),nums.at(right));
        }
        reverse(nums.begin()+left+1,nums.end());
        return nums;
    }
};

int main()
{
    vector<int> v={1,2,3};
    Solution s;
    vector<int> res;
    res=s.nextPermutation(v);
    for (vector<int>::iterator it = res.begin(); it != res.end(); it++)
    {
       cout<<*it<<" ";
    }
    //cout << "Hello world!" << endl;
    return 0;
}
```



END