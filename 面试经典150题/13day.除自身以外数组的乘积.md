# 除自身以外数组的乘积



给你一个整数数组 `nums`，返回 数组 `answer` ，其中 `answer[i]` 等于 `nums` 中除 `nums[i]` 之外其余各元素的乘积 。

题目数据 **保证** 数组 `nums`之中任意元素的全部前缀元素和后缀的乘积都在 **32 位** 整数范围内。

请 **不要使用除法，**且在 `O(n)` 时间复杂度内完成此题。

 

**示例 1:**

```
输入: nums = [1,2,3,4]
输出: [24,12,8,6]
```

**示例 2:**

```
输入: nums = [-1,1,0,-3,3]
输出: [0,0,9,0,0]
```

 

**提示：**

- `2 <= nums.length <= 105`
- `-30 <= nums[i] <= 30`
- 输入 **保证** 数组 `answer[i]` 在 **32 位** 整数范围内





```c++
class Solution {
private:
    int pre[100005];
    int h[100005];
    vector<int>res;
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        memset(pre,0,sizeof(pre));
        memset(h,0,sizeof(h));

        pre[0]=1;
        h[nums.size()-1]=1;

        for(int i=1;i<nums.size();i++)
        {
            pre[i]=pre[i-1]*nums[i-1];
        }

        for(int i=nums.size()-2;i>=0;i--)
        {
            h[i]=h[i+1]*nums[i+1];
        }

        for(int i=0;i<nums.size();i++)
        {
            res.emplace_back(pre[i]*h[i]);
        }
        return res;
    }
};
```

