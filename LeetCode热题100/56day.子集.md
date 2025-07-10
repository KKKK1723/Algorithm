# 子集

已解答

中等



相关标签

![premium lock icon](https://static.leetcode.cn/cn-frontendx-assets/production/_next/static/images/lock-a6627e2c7fa0ce8bc117c109fb4e567d.svg)相关企业



给你一个整数数组 `nums` ，数组中的元素 **互不相同** 。返回该数组所有可能的子集（幂集）。

解集 **不能** 包含重复的子集。你可以按 **任意顺序** 返回解集。

 

**示例 1：**

```
输入：nums = [1,2,3]
输出：[[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
```

**示例 2：**

```
输入：nums = [0]
输出：[[],[0]]
```

 

**提示：**

- `1 <= nums.length <= 10`
- `-10 <= nums[i] <= 10`
- `nums` 中的所有元素 **互不相同**





```C++
class Solution {

private:
    vector<vector<int>>e;
    vector<int>p;
public:
    vector<vector<int>> subsets(vector<int>& nums) {
   
        for(int i=0;i<=nums.size();i++)
        {
            dfs(nums,i,0);
        }
        
        return e;
    }


    void dfs(vector<int>& nums,int dex,int next)
    {
        if(p.size()==dex)
        {
            e.emplace_back(p);
            return;
        }

        for(int i=next;i<nums.size();i++)
        {
            p.emplace_back(nums[i]);
            dfs(nums,dex,i+1);
            p.pop_back();
        }
    }
    
};
```

