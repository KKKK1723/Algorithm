# 前 K 个高频元素





给你一个整数数组 `nums` 和一个整数 `k` ，请你返回其中出现频率前 `k` 高的元素。你可以按 **任意顺序** 返回答案。

 

**示例 1:**

```
输入: nums = [1,1,1,2,2,3], k = 2
输出: [1,2]
```

**示例 2:**

```
输入: nums = [1], k = 1
输出: [1]
```

 

**提示：**

- `1 <= nums.length <= 105`
- `k` 的取值范围是 `[1, 数组中不相同的元素的个数]`
- 题目数据保证答案唯一，换句话说，数组中前 `k` 个高频元素的集合是唯一的

 

```c++
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        unordered_map<int,int>mp;
        priority_queue<pair<int,int>,vector<pair<int,int>>,greater<pair<int,int>>>q;
        vector<int>res;
        for(auto& t:nums)
        {
            mp[t]++;
        }

        for(auto&[num,ans]:mp)
        {
            q.push({ans,num});
            if(q.size()>k)
            {
                q.pop();
            }
        }

        while(!q.empty()) {
            res.push_back(q.top().second); 
            q.pop();
        }
        return res;
    }
};
```

