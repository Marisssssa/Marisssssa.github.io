---
layout: post
title:  "Leetcode0016.threeSumCloest"
date:   2022-01-09
excerpt: "Leetcode最接近的三数之和."
tag:
- leetcode 
- 算法
comments: false
---

<center><b>0016.threeSumCloest.</b> </center>

# Leetcode题目0016.threeSumCloest

给你一个长度为 n 的整数数组 nums 和 一个目标值 target。请你从 nums 中选出三个整数，使它们的和与 target 最接近。

返回这三个数的和。

假定每组输入只存在恰好一个解。

<table><tr><td><img src="https://gitee.com/llesssssa/imagebed/raw/master/master/202201091609845.png" alt="16eg1" style="zoom:100%;"/></td><td><img src="C:\Users\Administrator\Desktop\mdimgs\16eg2.png" alt="16eg2" style="zoom:120%;"/></td></tr></table>

这道题和15题三数之和很类似，思想一致。

时间复杂度：$O(n^2)$

空间复杂度：$O(1)$

代码：

```c++
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

class Solution {
public:
    int threeSumClosest(vector<int>& nums, int target) {
        int result,left,right,diff,temp=99999;
        sort(nums.begin(),nums.end());
        for(int i=0;i<(int)nums.size();i++)
        {
            left=i+1;right=nums.size()-1;
            while(left<right)
            {
                int sum=nums.at(i)+nums.at(left)+nums.at(right);
                diff=abs(target-sum);
                if(diff<temp)
                    {result=sum;temp=diff;}
                if(sum==target)
                    return sum;
                else if(sum>target)
                    right--;
                else
                    left++;
            }
        }
        return result;
    }
};

int main()
{
    vector<int> v={1,2,5,10,11};
    int t=12;
    Solution s;
    int res=s.threeSumClosest(v,t);
    cout << res << endl;
    return 0;
}
```



END