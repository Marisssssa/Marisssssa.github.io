---
layout: post
title:  "Leetcode0018.fourSum"
date:   2022-01-10
excerpt: "Leetcode四数之和."
tag:
- leetcode 
- 算法
comments: false
---

<center><b>0018.fourSum.</b> </center>

# Leetcode题目0018.fourSum

给你一个由 n 个整数组成的数组 nums ，和一个目标值 target 。请你找出并返回满足下述全部条件且不重复的四元组 [nums[a], nums[b], nums[c], nums[d]] （若两个四元组元素一一对应，则认为两个四元组重复）：

0 <= a, b, c, d < n
a、b、c 和 d 互不相同
nums[a] + nums[b] + nums[c] + nums[d] == target
你可以按 任意顺序 返回答案 。

<table><tr><td><img src="https://s2.loli.net/2022/01/10/4kbAz2NJHxioEId.png" alt="18eg1" style="zoom:100%;" /></td><td><img src="https://s2.loli.net/2022/01/10/WIPaZmQovBGgj8K.png" alt="18eg2" style="zoom:100%;" /></td></tr></table>

这道题和前几题思想一致。

时间复杂度：$O(n^3)$

空间复杂度：$O(1)$

代码：

```c++
class Solution
{
public:
    vector<vector<int>> fourSum(vector<int>& nums, int target)
    {
        vector<vector<int>> result;
        sort(nums.begin(),nums.end());
        int left,right;
        if(nums.size()<4)
            return result;
        for(int i=0; i<(int)nums.size()-3; i++)
        {
            if(i>0&&nums.at(i)==nums.at(i-1))
            {
                continue;
            }
            if((long) nums.at(i)+nums.at(i+1)+nums.at(i+2)+nums.at(i+3)>target)
            {
                break;
            }
            if((long)nums.at(i)+nums.at(nums.size()-3)+nums.at(nums.size()-2)+nums.at(nums.size()-1)<target)
            {
                continue;
            }

            for(int j=i+1; j<(int)nums.size()-2; j++)
            {
                if(j>i+1&&nums.at(j)==nums.at(j-1))
                {
                    continue;
                }
                if((long)nums.at(i)+nums.at(j)+nums.at(j+1)+nums.at(j+2)>target)
                {
                    break;
                }
                if((long)nums.at(i)+nums.at(j)+nums.at(nums.size()-2)+nums.at(nums.size()-1)<target)
                {
                    continue;
                }
                else
                {
                    left=j+1;
                    right=nums.size()-1;
                    while(left<right)
                    {
                        int sum=nums.at(i)+nums.at(j)+nums.at(left)+nums.at(right);
                        if(sum==target)
                        {
                            result.push_back({nums.at(i),nums.at(j),nums.at(left),nums.at(right)});
                            while(left<right&&nums.at(left)==nums.at(left+1))
                            {
                                left++;
                            }
                            left++;
                            while(left<right&&nums.at(right)==nums.at(right-1))
                            {
                                right--;
                            }
                            right--;
                        }
                        else if(sum<target)
                            left++;
                        else
                            right--;
                    }
                }

            }


        }
        //set<vector<int>> s(result.begin(),result.end());
        //result.assign(s.begin(),s.end());
        return result;
    }
};
```



END