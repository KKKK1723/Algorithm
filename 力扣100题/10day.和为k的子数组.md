## 560. 和为 K 的子数组

**难度：中等**

### 题目描述

给你一个整数数组 `nums` 和一个整数 `k`，请你统计并返回该数组中和为 `k` 的子数组的个数。

子数组是数组中元素的连续非空序列。

---

### 示例

**示例 1：**  
输入：nums = [1,1,1], k = 2  
输出：2

**示例 2：**  
输入：nums = [1,2,3], k = 3  
输出：2

---

### 提示

- 1 <= nums.length <= 2 * 10⁴  
- -1000 <= nums[i] <= 1000  
- -10⁷ <= k <= 10⁷

```
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        int res=0;
        map<int,int>mp;
        int sum=0;
        mp[0]=1;
        for(int i=0;i<nums.size();i++)
        {
            sum+=nums[i];
            int tmp=sum-k;
            if(mp.find(tmp)!=mp.end())
            {
                res+=mp[tmp];
            }
            mp[sum]++;
        }
        return res;
    }
};
```
