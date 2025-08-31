# 柱状图中最大的矩形



给定 *n* 个非负整数，用来表示柱状图中各个柱子的高度。每个柱子彼此相邻，且宽度为 1 。

求在该柱状图中，能够勾勒出来的矩形的最大面积。

 

**示例 1:**

![img](https://assets.leetcode.com/uploads/2021/01/04/histogram.jpg)

```
输入：heights = [2,1,5,6,2,3]
输出：10
解释：最大的矩形为图中红色区域，面积为 10
```

**示例 2：**

![img](https://assets.leetcode.com/uploads/2021/01/04/histogram-1.jpg)

```
输入： heights = [2,4]
输出： 4
```

 

**提示：**

- `1 <= heights.length <=105`
- `0 <= heights[i] <= 104`





```C++
class Solution {
public:
    int largestRectangleArea(vector<int>& heights) {
        int n=heights.size();
        vector<int>left(n);
        vector<int>right(n,n);
        stack<int>q;

        for(int i=0;i<n;i++)
        {
            while(!q.empty()&&heights[q.top()]>=heights[i])
            {
                q.pop();
            }
            left[i]=(q.empty()?-1:q.top());
            q.push(i);
        }

        while (!q.empty()) {
            q.pop();
        }
        
        for(int i=n-1;i>=0;i--)
        {
            while(!q.empty()&&heights[q.top()]>=heights[i])
            {
                q.pop();
            }
            right[i]=(q.empty()?n:q.top());
            q.push(i);
        }

        int maxx=-1;
        for(int i=0;i<n;i++)
        {
            maxx=max(maxx,(right[i]-left[i]-1)*heights[i]);
        }
        return maxx;
    }
};
```

