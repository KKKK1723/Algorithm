# 128. 最长连续序列
  

---

## 题目描述

给定一个未排序的整数数组 `nums`，找出数字连续的最长序列（不要求序列元素在原数组中连续）的长度。



---

## 示例

### 示例 1

- 输入：`nums = [100, 4, 200, 1, 3, 2]`
- 输出：`4`
- 解释：最长数字连续序列是 `[1, 2, 3, 4]`，它的长度为 `4`。

### 示例 2

- 输入：`nums = [0, 3, 7, 2, 5, 8, 4, 6, 0, 1]`
- 输出：`9`

### 示例 3

- 输入：`nums = [1, 0, 1, 2]`
- 输出：`3`

---

## 提示

- `0 <= nums.length <= 10^5`
- `-10^9 <= nums[i] <= 10^9`

```
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        vector<int>t;
        map<int,int>mp;
        for(int i=0;i<nums.size();i++)
        {
            int tmp=nums[i];
            if(mp.count(tmp)==0)
            {
                mp[tmp]++;
                t.push_back(tmp);
            }
        }
        sort(t.begin(),t.end());
        // for(int i=0;i<t.size();i++)cout<<t[i]<<" ";
        // cout<<endl;
        if(t.size()==0)return 0;
        int maxlen=0;
        int nowlen=1;
        int now=t[0];
        if(t.size()==1)return 1;
        for(int i=1;i<t.size();i++)
        {
            if(t[i]==now+1)
            {
                nowlen++;
                now=t[i];
            }
            else
            {
                maxlen=max(maxlen,nowlen);
                nowlen=1;
                now=t[i];
            }
             maxlen=max(maxlen,nowlen);
        }
        return maxlen;
    }
};
```
