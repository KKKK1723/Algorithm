# 搜索旋转排序数组





整数数组 `nums` 按升序排列，数组中的值 **互不相同** 。

在传递给函数之前，`nums` 在预先未知的某个下标 `k`（`0 <= k < nums.length`）上进行了 **旋转**，使数组变为 `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]`（下标 **从 0 开始** 计数）。例如， `[0,1,2,4,5,6,7]` 在下标 `3` 处经旋转后可能变为 `[4,5,6,7,0,1,2]` 。

给你 **旋转后** 的数组 `nums` 和一个整数 `target` ，如果 `nums` 中存在这个目标值 `target` ，则返回它的下标，否则返回 `-1` 。

你必须设计一个时间复杂度为 `O(log n)` 的算法解决此问题。

 

**示例 1：**

```
输入：nums = [4,5,6,7,0,1,2], target = 0
输出：4
```

**示例 2：**

```
输入：nums = [4,5,6,7,0,1,2], target = 3
输出：-1
```

**示例 3：**

```
输入：nums = [1], target = 0
输出：-1
```

 

**提示：**

- `1 <= nums.length <= 5000`
- `-104 <= nums[i] <= 104`
- `nums` 中的每个值都 **独一无二**
- 题目数据保证 `nums` 在预先未知的某个下标上进行了旋转
- `-104 <= target <= 104`



```c++
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int n = nums.size();
        if (n == 0) return -1;
        if (n == 1) return nums[0] == target ? 0 : -1;

        //找边界
        if(nums[0]>nums[n-1])
        {
            int dex=find_bj(nums);
            if(target>=nums[0])//左半边
            {
                return bs(nums,0,dex-1,target);
            }
            else{//右半边
                return bs(nums,dex,n-1,target);
            }
        }
        else{
            return bs(nums,0,n-1,target);
        }
        
    }

    int find_bj(vector<int>& nums)
    {
        int left=-1;
        int right=nums.size();
        while(left+1!=right)
        {
            int mid=(left+right)/2;
            if(nums[mid]>=nums[0])
            {
                left=mid;
            }
            else if(nums[mid]<nums[0])
            {
                right=mid;
            }
        }

        return right;
    }

    int bs(vector<int>& nums,int start,int end, int target)
    {
        int left=start-1,right=end+1;
        while(left+1!=right)
        {
            int mid=(left+right)/2;
            if(nums[mid]<target)
            {
                left=mid;
            }
            else{
                right=mid;
            }
        }

        if(right>=start&&right<=end&&nums[right]==target)
        {
            return right;
        }
        return -1;
    }
};
```

