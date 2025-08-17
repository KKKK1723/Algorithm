# 最长回文子串



给你一个字符串 `s`，找到 `s` 中最长的 回文 子串。

 

**示例 1：**

```
输入：s = "babad"
输出："bab"
解释："aba" 同样是符合题意的答案。
```

**示例 2：**

```
输入：s = "cbbd"
输出："bb"
```

 

**提示：**

- `1 <= s.length <= 1000`
- `s` 仅由数字和英文字母组成



```c++
class Solution {
public:
    string longestPalindrome(string s) {
        if(s.size()==1)return s;
        bool dp[1100][1100];
        memset(dp,0,sizeof(dp));
        int n=s.size();
        for(int i=0;i<n;i++)
        {
            dp[i][i]=1;
        }

        int maxx=1;
        int t=0;

        for(int len=2;len<=n;len++)
        {
            for(int left=0;left<n;left++)
            {
                int right=len+left-1;
                if(right>=n)break;

                if(s[left]!=s[right])
                {
                    dp[left][right]=false;
                }
                else
                {
                    if(right-left<3)
                    {
                        dp[left][right]=true;
                    }
                    else{
                        dp[left][right]=dp[left+1][right-1];
                    }
                }

                if(dp[left][right]&&right-left+1>maxx)
                {
                    maxx=right-left+1;
                    t=left;
                }
            }
        }
        return s.substr(t,maxx);
    }
};
```

