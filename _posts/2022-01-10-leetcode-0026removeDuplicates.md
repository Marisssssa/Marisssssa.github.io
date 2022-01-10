---
layout: post
title:  "Leetcode0026.removeDuplicates"
date:   2022-01-10
excerpt: "Leetcode删除有序数组中的重复项."
tag:
- leetcode 
- 算法
comments: false
---

<center><b>0026.removeDuplicates.</b> </center>

# Leetcode题目0026.removeDuplicates

给你一个有序数组 nums ，请你 原地 删除重复出现的元素，使每个元素 只出现一次 ，返回删除后数组的新长度。

不要使用额外的数组空间，你必须在 原地 修改输入数组 并在使用 O(1) 额外空间的条件下完成。

![26eg1](https://s2.loli.net/2022/01/10/eLRB6IpskQNMzmb.png)

![26eg2](https://s2.loli.net/2022/01/10/YlXqekKGb41gMfm.png)

使用一个快指针和一个慢指针，从第二个数字开始遍历，如果与前一个数字相同，则快指针往后走一步，否则两个指针都走一步，且将快指针指的数值赋值到慢指针的指向。最终慢指针的数值就为数组的长度。

时间复杂度：$O(n)$

空间复杂度：$O(1)$

代码：

```c++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if(nums.size()==0)
            return 0;
        int slow=1,fast=1;
        while(fast<(int)nums.size())
        {
            if(nums.at(fast)!=nums.at(fast-1))
            {
                nums.at(slow)=nums.at(fast);
                slow++;
            }
            fast++;
        }
        return slow;
    }
};
```



END