# 283. 移动零


---

## 题目描述

给定一个数组 `nums`，编写一个函数将所有 `0` 移动到数组的末尾，同时保持非零元素的相对顺序。

请注意，必须在 **不复制数组** 的情况下 **原地对数组进行操作**。

---

## 示例

### 示例 1

- 输入：`nums = [0,1,0,3,12]`
- 输出：`[1,3,12,0,0]`

### 示例 2

- 输入：`nums = [0]`
- 输出：`[0]`

---

## 提示

- `1 <= nums.length <= 10^4`
- `-2^31 <= nums[i] <= 2^31 - 1`

```
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        long long cnt=0;
        vector<int>p;
        for(int i=0;i<nums.size();i++)
        {
            if(nums[i]==0)
            {
                nums.erase(nums.begin()+i);
                //nums.push_back(0);
                cnt++;
                i--;
            }
        }
        while(cnt--)nums.push_back(0);
       
    }
};
```
