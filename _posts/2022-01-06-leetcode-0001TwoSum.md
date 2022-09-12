---
title:  "Leetcode0001.TwoSum"
tags: leetcode 算法
---



给定一个整数数组 nums 和一个整数目标值 target，请你在该数组中找出 和为目标值 target  的那 两个 整数，并返回它们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。

<!--more-->

| ![twosumeg1](https://gitee.com/llesssssa/imagebed/raw/master/master/twosumeg1.png) | ![twosumeg2](https://gitee.com/llesssssa/imagebed/raw/master/master/twosumeg2.png) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![twosumeg3](https://gitee.com/llesssssa/imagebed/raw/master/master/twosumeg3.png) |                                                              |

### 1.自己编译测试代码

a.暴力解法（直接循环）：

时间复杂度：$O(n^{2})$


设定tag，不需要循环完整个数据

```c++
#include <iostream>
#include <vector>
using namespace std;

class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        bool findOrNot=false;//判断是否已经找到
        vector<int> result;
        for(int i=0;i<nums.size();i++)
        {
            for(int j=0;j<nums.size();j++)
            {
                if(i!=j&&nums.at(i)+nums.at(j)==target)//等于目标值且不能是同一个
                {
                    findOrNot=true;//找到的话改tag
                    result={i,j};
                }
                if(findOrNot==true)//跳出循环，不必循环完
                    break;
            }
            if(findOrNot==true)
                break;
        }
        return result;
    }
};

int main() {
    Solution s;
    vector<int> v={2,7,11,15};
    vector<int> res;
    int target=9;
    res=s.twoSum(v,target);
    for(auto i=res.begin();i<res.end();i++)//使用迭代器遍历容器
    {
        cout<<*i<<" ";
    }
    return 0;
}
```

b.通过找差值的方法来降低时间复杂度，只遍历一次数据

时间复杂度：$O(n)$

```c++
#include <iostream>
#include <vector>
#include <map>
#include <algorithm>

using namespace std;

class Solution{
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> result;
        map<int,int> searchMap;//记录所有未找到匹配数据的数值和索引
        int differ;//差值
        for(int i=0;i<nums.size();i++)
        {
            differ=target-nums.at(i);
            if(searchMap.find(differ)!=searchMap.end())//找数据里是否有对应的差值项
            {
                result={i,searchMap[differ]};
                sort(result.begin(),result.end());//索引大小排序
                return result;
            }
            searchMap[nums.at(i)]=i;//未找到则进行记录
        }
        return {};
    }
};

int main()
{
    Solution s;
    vector<int> v={2,7,11,15};
    vector<int> res;
    int target=9;
    res=s.twoSum(v,target);
    for(auto i=res.begin();i<res.end();i++)
    {
        cout<<*i<<" ";
    }
    return 0;
}
```

### 2.Leetcode提交代码

a.暴力解法

```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        bool findOrNot=false;//判断是否已经找到
        vector<int> result;
        for(int i=0;i<nums.size();i++)
        {
            for(int j=0;j<nums.size();j++)
            {
                if(i!=j&&nums.at(i)+nums.at(j)==target)//等于目标值且不能是同一个
                {
                        result={i,j};
                        findOrNot=true;//找到的话改tag
                }
                if(findOrNot==true)//跳出循环，不必循环完
                    break;
            }
            if(findOrNot==true)
                break;
        }
        return result;
    }
};
```

b.低时间复杂度方法

```c++
class Solution{
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> result;
        map<int,int> searchMap;//记录所有未找到匹配数据的数值和索引
        int differ;//差值
        for(int i=0;i<nums.size();i++)
        {
            differ=target-nums.at(i);
            if(searchMap.find(differ)!=searchMap.end())//找数据里是否有对应的差值项
            {
                result={i,searchMap[differ]};
                sort(result.begin(),result.end());//索引大小排序
                return result;
            }
            searchMap[nums.at(i)]=i;//未找到则进行记录
        }
        return {};
    }
};
```



END