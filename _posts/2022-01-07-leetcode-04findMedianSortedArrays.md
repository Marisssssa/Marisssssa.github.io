---
layout: post
title:  "Leetcode04.findMedianSortedArrays"
date:   2022-01-07
excerpt: "Leetcode寻找中位数."
tag:
- leetcode 
- 算法
comments: false
---

<center><b>04.findMedianSortedArrays.</b> </center>

# Leetcode题目04.findMedianSortedArrays

题目：寻找两个正序数组的中位数

给定两个大小分别为 m 和 n 的正序（从小到大）数组 nums1 和 nums2。请你找出并返回这两个正序数组的 中位数 。

算法的时间复杂度应该为 O(log (m+n)) 。

| ![04eg1](https://gitee.com/llesssssa/imagebed/raw/master/master/04eg1.png) | ![04eg2](https://gitee.com/llesssssa/imagebed/raw/master/master/04eg2.png) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![04eg3](https://gitee.com/llesssssa/imagebed/raw/master/master/04eg3.png) | ![04eg4](https://gitee.com/llesssssa/imagebed/raw/master/master/04eg4.png) |

利用二分法来解题。

设定A和B来将两个数组都分为两部分，使得nums1左半部分和nums2左半部分的数字个数为两个数组个数之和的一半，同时nums1的A所指的数要比nums2的B所指的下一个数小，nums2的B所指的数要比nums1的A所指的下一个数要小，即保证两个数组的左侧的所有数字比右侧的所有数字都要小，如果没满足就继续向左或者向右二分分割。最后，选取AB所指的数字较大者为中位数，如果为总数偶数个，则选取较大者即它的下一位取均值。其中需要注意，若A到达了nums1最左侧，则可能是图2的情况，则结果取nums2的B所指的数字即可；若B到达了nums2最左侧，则可能是图1的情况，则结果取nums1的A所指的数字即可。

<table>
    <tr><td><img src="https://gitee.com/llesssssa/imagebed/raw/master/master/202201081304741.png" alt="A=0" style="zoom:75%;" />&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp图1</td><td><img src="https://gitee.com/llesssssa/imagebed/raw/master/master/202201081305934.png" alt="B=0" style="zoom:75%;" />&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp图2</td></tr>
</table>

代码：

```c++
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

class Solution
{
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2)
    {
        vector<int> v;
        if(nums1.size()>nums2.size())
        {
            v.assign(nums1.begin(),nums1.end());
            nums1.assign(nums2.begin(),nums2.end());
            nums2.assign(v.begin(),v.end());
        }

        int A,B;
        double result,result_;
        int nums1Start=0,nums1End=nums1.size();
        //int canContinue=0;
        while(nums1Start<=nums1End)
        {
            A=nums1Start+((nums1End-nums1Start)/2);
            B=(nums1.size()+nums2.size()+1)/2-A;
            if(A>0&&nums1.at(A-1)>nums2.at(B))
            {
                nums1End=A-1;
            }
            else if(A<(int)nums1.size()&&nums1.at(A)<nums2.at(B-1))
            {
                nums1Start=A+1;
            }
            else
            {
                if(A==0)
                    result=nums2.at(B-1);
                else if(B==0)
                    result=nums1.at(A-1);
                else
                    result=max(nums1.at(A-1),nums2.at(B-1));
                if((nums1.size()+nums2.size())%2!=0)
                    return result;
                else
                    if(A==(int)nums1.size())
                        result_=nums2.at(B);
                    else if(B==(int)nums2.size())
                        result_=nums1.at(A);
                    else
                        result_=min(nums1.at(A),nums2.at(B));
                    return (result+result_)/2.0;
            }
        }
        return 0;
    }
};

int main()
{
    double res=0;
    Solution s;
    //vector<int> v1= {3,13,15,18};
    //vector<int> v2= {2,6,7,9,11,13,15};
    vector<int> v1= {1,2};
    vector<int> v2= {3,4};
    res=s.findMedianSortedArrays(v1,v2);
    cout<<res;
    return 0;
}
```



END