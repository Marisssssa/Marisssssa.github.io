---
layout: post
title:  "Leetcode0036.isValidSudoku"
date:   2022-01-22
excerpt: "Leetcode.有效的数独"
tag:
- leetcode 
- 算法
comments: false
---

<center><b>0036.isValidSudoku.</b> </center>

# Leetcode题目0036.isValidSudoku

请你判断一个 9 x 9 的数独是否有效。只需要 根据以下规则 ，验证已经填入的数字是否有效即可。

数字 1-9 在每一行只能出现一次。
数字 1-9 在每一列只能出现一次。
数字 1-9 在每一个以粗实线分隔的 3x3 宫内只能出现一次。（请参考示例图）


注意：

一个有效的数独（部分已被填充）不一定是可解的。
只需要根据以上规则，验证已经填入的数字是否有效即可。
空白格用 '.' 表示。

![36eg1](https://gitee.com/llesssssa/imagebed/raw/master/master/202201231601972.png)

![36eg2](https://gitee.com/llesssssa/imagebed/raw/master/master/202201231601398.png)

解法：

利用哈希的思想来判定某行或者某列或者某个3*3的格子里是否有重复值。

时间复杂度：$O(1)$

空间复杂度：$O(1)$

代码：

```c++
#include <iostream>
#include <string.h>
#include <vector>

using namespace std;

class Solution {
public:
    bool isValidSudoku(vector<vector<char>>& board) {
        int row[9][9];
        int col[9][9];
        int nineBox[3][3][9];
        char ch;
        int ch_value;
        memset(row,0,sizeof(row));
        memset(col,0,sizeof(col));
        memset(nineBox,0,sizeof(nineBox));
        for(int i=0;i<9;i++)
        {
            for(int j=0;j<9;j++)
            {
                ch=board[i][j];
                if(ch!='.')
                {
                    ch_value=ch-'0'-1;
                    row[i][ch_value]++;
                    col[j][ch_value]++;
                    nineBox[i/3][j/3][ch_value]++;
                    if(row[i][ch_value]>1||col[j][ch_value]>1||nineBox[i/3][j/3][ch_value]>1)
                        return false;
                }
            }
        }
        return true;
    }
};

int main()
{
    vector<vector<char>> a={{'5','3','.','.','7','.','.','.','.'},
    {'6','.','.','1','9','5','.','.','.'},
    {'.','9','8','.','.','.','.','6','.'},
    {'8','.','.','.','6','.','.','.','3'},
    {'4','.','.','8','.','3','.','.','1'},
    {'7','.','.','.','2','.','.','.','6'},
    {'.','6','.','.','.','.','2','8','.'},
    {'.','.','.','4','1','9','.','.','5'},
    {'.','.','.','.','8','.','.','7','9'}};
    //memset(a,0,sizeof(a));
    for(int i=0;i<9;i++)
    {
        cout<<endl;
        for(int j=0;j<9;j++)
        {
            cout<<a[i][j]<<" ";
        }
    }
    Solution s;
    bool res;
    res=s.isValidSudoku(a);
    cout << res << endl;
    return 0;
}
```



END