# 42. 接雨水（Trapping Rain Water）

**难度：困难**

## 题目描述

给定 `n` 个非负整数，表示每个宽度为 1 的柱子的高度图，计算按此排列的柱子，在下雨之后能接多少雨水。
![](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/22/rainwatertrap.png) 

## 示例 1：

输入：`height = [0,1,0,2,1,0,1,3,2,1,2,1]`  
输出：`6`  
解释：上面是由数组 `[0,1,0,2,1,0,1,3,2,1,2,1]` 表示的高度图，在这种情况下，可以接 6 个单位的雨水（蓝色部分表示雨水）。

## 示例 2：

输入：`height = [4,2,0,3,2,5]`  
输出：`9`

## 提示：

- `n == height.length`
- `1 <= n <= 2 * 10^4`
- `0 <= height[i] <= 10^5`
```
class Solution {
public:
    int trap(vector<int>& height) {
        const int maxx=2e4+10;
        int preleft[maxx];
        int preright[maxx];
        memset(preleft,0,sizeof(preleft));
        memset(preright,0,sizeof(preright));
        for(int i=0;i<height.size();i++)
        {
            if(i==0)
            {
                preleft[i]=height[i];
            }
            else
            {
                preleft[i]=max(preleft[i-1],height[i]);
            }
        }
        for(int i=height.size()-1;i>=0;i--)
        {
            if(i==height.size()-1)
            {
                preright[i]=height[i];
            }
            else
            {
                preright[i]=max(preright[i+1],height[i]);
            }
        }

        int sum=0;
        for(int i=0;i<height.size();i++)
        {
            if(preleft[i]==height[i]||preright[i]==height[i])continue;

            int tmp=min(preleft[i],preright[i]);
            sum+=tmp-height[i];
        }
        return sum;
    }
};

```


