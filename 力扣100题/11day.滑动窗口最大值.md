# 239. 滑动窗口最大值

## 题目描述

给你一个整数数组 `nums`，有一个大小为 `k` 的滑动窗口从数组的最左侧移动到数组的最右侧。你只可以看到在滑动窗口内的 `k` 个数字。

滑动窗口每次只向右移动一位。

返回**滑动窗口中的最大值**组成的数组。

---

## 示例

### 示例 1：

**输入：**
nums = [1,3,-1,-3,5,3,6,7], k = 3



**输出：**
[3,3,5,5,6,7]

yaml
复制
编辑

**解释：**

| 滑动窗口的位置         | 最大值 |
|------------------------|--------|
| [1  3  -1] -3  5  3  6  7 | 3      |
| 1 [3  -1  -3] 5  3  6  7 | 3      |
| 1  3 [-1  -3  5] 3  6  7 | 5      |
| 1  3  -1 [-3  5  3] 6  7 | 5      |
| 1  3  -1  -3 [5  3  6] 7 | 6      |
| 1  3  -1  -3  5 [3  6  7]| 7      |

---

### 示例 2：

**输入：**
nums = [1], k = 1



**输出：**
[1]



---

## 提示：

- 1 <= nums.length <= 10⁵  
- -10⁴ <= nums[i] <= 10⁴  
- 1 <= k <= nums.length

```
class Solution {
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        vector<int>end;
        deque<int>qmax;
        for(int i=0;i<k;i++)
        {
            if(i>=nums.size())break;
            int tmp=nums[i];
            while(!qmax.empty()&&tmp>qmax.back())
            {
                qmax.pop_back();
            }
            qmax.push_back(tmp);
        }
        end.push_back(qmax.front());

        for(int i=k;i<nums.size();i++)
        {
            int tmp=nums[i];
            int yq=nums[i-k];
            if(yq==qmax.front())
            {
                qmax.pop_front();
            }

            while(!qmax.empty()&&tmp>qmax.back())
            {
                qmax.pop_back();
            }
            qmax.push_back(tmp);
            end.push_back(qmax.front());
        }

        return end;
    }
};
```
