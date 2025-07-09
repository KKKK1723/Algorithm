# 全排列



给定一个不含重复数字的数组 `nums` ，返回其 *所有可能的全排列* 。你可以 **按任意顺序** 返回答案。

 

**示例 1：**

```
输入：nums = [1,2,3]
输出：[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

**示例 2：**

```
输入：nums = [0,1]
输出：[[0,1],[1,0]]
```

**示例 3：**

```
输入：nums = [1]
输出：[[1]]
```

 

**提示：**

- `1 <= nums.length <= 6`
- `-10 <= nums[i] <= 10`
- `nums` 中的所有整数 **互不相同**



```c++
class Solution {
private:
    bool vis[11];
    vector<vector<int>>e;

public:
    vector<vector<int>> permute(vector<int>& nums) {
        memset(vis,0,sizeof(vis));
        
        vector<int>tmp;
        dfs(nums,tmp);
        return e;
    }

    void dfs(vector<int>& nums,vector<int>& tmp)
    {
        if(tmp.size()==nums.size())
        {
            e.emplace_back(tmp);
        }

        for(int i=0;i<nums.size();i++)
        {
            if(vis[i])continue;
            vis[i]=1;
            tmp.emplace_back(nums[i]);
            dfs(nums,tmp);
            tmp.pop_back();
            vis[i]=0;
        }
    }
};
```

