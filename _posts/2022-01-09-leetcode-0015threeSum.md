---
layout: post
title:  "Leetcode0015.threeSum"
date:   2022-01-09
excerpt: "Leetcode三数之和."
tag:
- leetcode 
- 算法
comments: false
---

<center><b>0015.threeSum.</b> </center>

# Leetcode题目0015.threeSum

题目：三数之和

给你一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？请你找出所有和为 0 且不重复的三元组。

注意：答案中不可以包含重复的三元组。

| ![15eg1](https://gitee.com/llesssssa/imagebed/raw/master/master/202201091500908.png) | ![15eg2](https://gitee.com/llesssssa/imagebed/raw/master/master/202201091500778.png) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![15eg3](https://gitee.com/llesssssa/imagebed/raw/master/master/202201091500026.png) |                                                              |

1.暴力解法：

未通过，时间超出限制。

时间复杂度：$O(n^3)$

```c++
#include <iostream>
#include <vector>
#include <set>
#include <algorithm>

using namespace std;

class Solution
{
public:
    vector<vector<int>> threeSum(vector<int>& nums)
    {
        vector<vector<int>> result;
        int num=0;
        for(int i=0; i<(int)nums.size(); i++)
        {
            for(int j=i+1; j<(int)nums.size(); j++)
            {
                for(int k=j+1; k<(int)nums.size(); k++)
                {
                    if(nums.at(i)+nums.at(j)+nums.at(k)==0&&i!=j&&i!=k&&j!=k)
                    {
                        vector<int> a={nums.at(i),nums.at(j),nums.at(k)};
                        sort(a.begin(),a.end());
                        result.push_back(a);
                        num=num+1;
                    }
                }
            }
        }
        set<vector<int>> s(result.begin(),result.end());
        result.assign(s.begin(),s.end());
        return result;
    }
};

int main()
{
    Solution s;
    vector<int> v= {-1,0,1,2,-1,-4};
    vector<vector<int>> res;
    res=s.threeSum(v);
    for (vector<vector<int>>::iterator it = res.begin(); it != res.end(); it++)
    {
        for (vector<int>::iterator itit = (*it).begin(); itit != (*it).end(); itit++)
        {
            cout << *itit <<" ";
        }
        cout<<endl;

    }
    return 0;
}
```

2.如果nums的长度小于3直接输出空向量即可。对nums进行排序，升序保证了左边的数小于右边的数，当第一个数字循环到大于0的情况时，可以直接跳出循环。

利用一个for循环来设定第一个数字，然后利用两个指针left和right来找剩下两个数字，left从第一个数字的下一个数字开始，right从nums尾开始，判断三数之和是否等于0，等于0则记录，且更新left和right指针到下一位置，如果和小于0，则left向右移，和大于0，则right向左移。如此循环。

在下列代码中，我选择的是全部找完之后利用set来去重，但时间和空间上不占优势，可以在寻找的过程中，利用while来判断重复值，这样的话，时间和空间可以在nums很大的时候省很多。

时间复杂度：$O(n^2)$

空间复杂度：$O(n)$ 如果使用寻找过程中去重值的话就为：$O(1)$

代码：

```c++
#include <iostream>
#include <vector>
#include <algorithm>
#include <set>

using namespace std;

class Solution
{
public:
    vector<vector<int>> threeSum(vector<int>& nums)
    {
        vector<vector<int>> result;
        int left,right;
        if(nums.size()<3)
            return result;
        sort(nums.begin(),nums.end());
        int i;
        for(i=0;i<(int)nums.size();i++)
        {
            if(nums.at(i)>0)
                break;
            else
                left=i+1;right=nums.size()-1;
                while(left<right)
                {
                    int sum=nums.at(i)+nums.at(left)+nums.at(right);
                    if(sum==0)
                    {
                        result.push_back({nums.at(i),nums.at(left),nums.at(right)});
                        left++;right--;
                    }
                    else if(sum>0)
                        right--;
                    else
                        left++;
                }
        }
        set<vector<int>> s(result.begin(),result.end());
        result.assign(s.begin(),s.end());
        return result;
    }
};

int main()
{
    Solution s;
    vector<int> v= {-1,0,1,2,-1,-4};
    vector<vector<int>> res;
    res=s.threeSum(v);
    for (vector<vector<int>>::iterator it = res.begin(); it != res.end(); it++)
    {
        for (vector<int>::iterator itit = (*it).begin(); itit != (*it).end(); itit++)
        {
            cout << *itit <<" ";
        }
        cout<<endl;

    }
    return 0;
}
```



END