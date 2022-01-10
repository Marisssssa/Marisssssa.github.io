---
layout: post
title:  "Leetcode0027.removeElement"
date:   2022-01-10
excerpt: "Leetcode移除元素."
tag:
- leetcode 
- 算法
comments: false
---

<center><b>0027.removeElement.</b> </center>

# Leetcode题目0027.removeElement

给你一个数组 nums 和一个值 val，你需要 原地 移除所有数值等于 val 的元素，并返回移除后数组的新长度。

不要使用额外的数组空间，你必须仅使用 O(1) 额外空间并 原地 修改输入数组。

元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。

<table><tr><td><img src="https://s2.loli.net/2022/01/10/rzX7mGShdxTsRjc.png" alt="27eg1" style="zoom:120%;" /></td><td><img src="https://s2.loli.net/2022/01/10/W9rFjxVkcpXRSZh.png" alt="27eg2" style="zoom:120%;" /></td></tr></table>

与0026题移除重复元素思想一致。

时间复杂度：$O(n)$

空间复杂度：$O(1)$

代码：

```c++
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        if(nums.size()==0)
            return 0;
        int slow=0,fast=0;
        while(fast<(int)nums.size())
        {
            if(nums.at(fast)!=val)
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