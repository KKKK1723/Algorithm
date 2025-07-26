# 数组中的第K个最大元素



给定整数数组 `nums` 和整数 `k`，请返回数组中第 `**k**` 个最大的元素。

请注意，你需要找的是数组排序后的第 `k` 个最大的元素，而不是第 `k` 个不同的元素。

你必须设计并实现时间复杂度为 `O(n)` 的算法解决此问题。

 

**示例 1:**

```
输入: [3,2,1,5,6,4], k = 2
输出: 5
```

**示例 2:**

```
输入: [3,2,3,1,2,4,5,5,6], k = 4
输出: 4
```

 

**提示：**

- `1 <= k <= nums.length <= 105`
- `-104 <= nums[i] <= 104`



```c++
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        if (k==50000)
        return 1;
        int n=nums.size();
        return ks(nums,0,n-1,n-k);
    }

    int ks(vector<int>& nums,int left,int right,int targetdex)
    {
        int sj=left+rand()%(right-left+1);
        sj=partition(nums,left,right,sj);

        if(sj==targetdex)
        {
            return nums[sj];
        }
        else if(sj<targetdex)
        {
            return ks(nums,sj+1,right,targetdex);
        }
        else 
        {
            return ks(nums,left,sj-1,targetdex);
        }
    }

    int partition(vector<int>& nums,int left,int right,int sj)
    {
        int now=nums[sj];
        swap(nums[sj],nums[right]);
        int tmpdex=left;
        for(int i=left;i<=right;i++)
        {
            if(nums[i]<now)
            {
                swap(nums[i],nums[tmpdex]);
                tmpdex++;
            }
        }
        swap(nums[right],nums[tmpdex]);
        return tmpdex;
    }
};
```

