# 238. 除自身以外数组的乘积
## 中等

给你一个整数数组 nums，返回 数组 answer ，其中 answer[i] 等于 nums 中除 nums[i] 之外其余各元素的乘积 。

题目数据 保证 数组 nums之中任意元素的全部前缀元素和后缀的乘积都在  32 位 整数范围内。

请 不要使用除法，且在 O(n) 时间复杂度内完成此题。

 ---

### 示例 1:

输入: nums = [1,2,3,4]
输出: [24,12,8,6]
示例 2:

输入: nums = [-1,1,0,-3,3]
输出: [0,0,9,0,0]
 

提示：

2 <= nums.length <= 105  
-30 <= nums[i] <= 30  
输入 保证 数组 answer[i] 在  32 位 整数范围内    
输入: nums = [1,2,3,4]    
输出: [24,12,8,6]    

解释：  
- 除 `nums[0] = 1` 外的乘积是 `2×3×4 = 24`  
- 除 `nums[1] = 2` 外的乘积是 `1×3×4 = 12`  
- 除 `nums[2] = 3` 外的乘积是 `1×2×4 = 8`  
- 除 `nums[3] = 4` 外的乘积是 `1×2×3 = 6`

---

### 示例 2:

输入: nums = [-1,1,0,-3,3]  
输出: [0,0,9,0,0]  

 ```
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int left[100005];
        int right[100005];
        memset(left,1,sizeof(left));
        memset(right,1,sizeof(right));

        int tmp=1;
        for(int i=0;i<nums.size();i++)
        {
            left[i]=tmp;
            tmp*=nums[i];
        }

        tmp=1;
        for(int i=nums.size()-1;i>=0;i--)
        {
            right[i]=tmp;
            tmp*=nums[i];
        }

        vector<int>end;
        for(int i=0;i<nums.size();i++)
        {
            end.push_back(left[i]*right[i]);
        }

        return end;
    }
};
```
