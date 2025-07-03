# 56. 合并区间

**难度：中等**

## 题目描述

以数组 `intervals` 表示若干个区间的集合，其中单个区间为 `intervals[i] = [starti, endi]`。请你合并所有重叠的区间，并返回一个不重叠的区间数组，该数组需恰好覆盖输入中的所有区间。

---

## 示例

**示例 1：**
```
输入：intervals = [[1,3],[2,6],[8,10],[15,18]]
输出：[[1,6],[8,10],[15,18]]
解释：区间 [1,3] 和 [2,6] 重叠, 将它们合并为 [1,6].
```

**示例 2：**
```
输入：intervals = [[1,4],[4,5]]
输出：[[1,5]]
解释：区间 [1,4] 和 [4,5] 可被视为重叠区间。
```

---

## 提示

- 1 <= intervals.length <= 10^4
- intervals[i].length == 2
- 0 <= starti <= endi <= 10^4

---

```
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        sort(intervals.begin(), intervals.end(), [](const vector<int>& a, const vector<int>& b) {
            return a[0] < b[0];
        });
        vector<vector<int>> end;
        bool vis[intervals.size()];
        memset(vis,0,sizeof(vis));

        for(int i=0;i<intervals.size();i++)
        {
            if(vis[i])continue;
            int right=intervals[i][1];
            int l=intervals[i][0];
            for(int j=i+1;j<intervals.size();j++)
            {
                if(vis[j])continue;
                if(intervals[j][0]>right)continue;
                
                right=max(right,intervals[j][1]);
                
                vis[j]=1;
            }
            end.push_back({l,right});
        }

        return end;
    }
};
```
