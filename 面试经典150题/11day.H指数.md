#  H 指数



提示



给你一个整数数组 `citations` ，其中 `citations[i]` 表示研究者的第 `i` 篇论文被引用的次数。计算并返回该研究者的 **`h` 指数**。

根据维基百科上 [h 指数的定义](https://baike.baidu.com/item/h-index/3991452?fr=aladdin)：`h` 代表“高引用次数” ，一名科研人员的 `h` **指数** 是指他（她）至少发表了 `h` 篇论文，并且 **至少** 有 `h` 篇论文被引用次数大于等于 `h` 。如果 `h` 有多种可能的值，**`h` 指数** 是其中最大的那个。

 

**示例 1：**

```
输入：citations = [3,0,6,1,5]
输出：3 
解释：给定数组表示研究者总共有 5 篇论文，每篇论文相应的被引用了 3, 0, 6, 1, 5 次。
     由于研究者有 3 篇论文每篇 至少 被引用了 3 次，其余两篇论文每篇被引用 不多于 3 次，所以她的 h 指数是 3。
```

**示例 2：**

```
输入：citations = [1,3,1]
输出：1
```

 

**提示：**

- `n == citations.length`
- `1 <= n <= 5000`
- `0 <= citations[i] <= 1000`





```c++
class Solution {
public:
    int hIndex(vector<int>& citations) {
        if(citations.size()==1)
        {
            if(citations[0]==0)return 0;
            return 1;
        }
        

        sort(citations.begin(),citations.end());
        int left=-1,right=citations.size()+1;
        //找h
        while(left+1!=right)
        {
            int mid=(left+right)/2;
            if(check(mid,citations))
            {
                left=mid;
            }
            else
            {
                right=mid;
            }
        }
        return left;
    }

    //找有多少个是大于等于num的
    bool check(int num,vector<int>& citations)
    {
        int l=-1,r=citations.size();
        while(l+1!=r)
        {
            int m=(l+r)/2;
            if(citations[m]>=num)
            {
                r=m;
            }
            else{
                l=m;
            }
        }

        int sum=citations.size()-r;
        return sum>=num;
    }
};
```

