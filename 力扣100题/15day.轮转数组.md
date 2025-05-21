# 189. 轮转数组（Rotate Array）

**难度：中等**  
**标签：数组、数学、双指针、模拟**  

---

## 🧾 题目描述

给定一个整数数组 `nums`，将数组中的元素 **向右轮转** `k` 个位置，其中 `k` 是非负数。

---

## 📥 示例

### 示例 1:
输入: nums = [1,2,3,4,5,6,7], k = 3
输出: [5,6,7,1,2,3,4]

解释:  
向右轮转 1 步: [7,1,2,3,4,5,6]  
向右轮转 2 步: [6,7,1,2,3,4,5]  
向右轮转 3 步: [5,6,7,1,2,3,4]  


### 示例 2:  

输入: nums = [-1,-100,3,99], k = 2  
输出: [3,99,-1,-100]  

解释:  
向右轮转 1 步: [99,-1,-100,3]  
向右轮转 2 步: [3,99,-1,-100]  


---

## 📌 提示

- `1 <= nums.length <= 10⁵`  
- `-2³¹ <= nums[i] <= 2³¹ - 1`  
- `0 <= k <= 10⁵`

---

```
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        int res=k%(nums.size());
        vector<int>p(nums.size()+1);
        for(int i=0;i<nums.size();i++)
        {
            p[i]=nums[i];
        }

        if(k!=0)
        {
            for(int i=0;i<nums.size();i++)
            {
                int dex;
                if(i-res<0)
                {
                    dex=nums.size()-1-(abs(i-res)-1);
                }
                else
                {
                    dex=i-res;
                }
                nums[i]=p[dex];
            }
        }
        
    }
};
```
