# 分割回文串





给你一个字符串 `s`，请你将 `s` 分割成一些 子串，使每个子串都是 **回文串** 。返回 `s` 所有可能的分割方案。

 

**示例 1：**

```
输入：s = "aab"
输出：[["a","a","b"],["aa","b"]]
```

**示例 2：**

```
输入：s = "a"
输出：[["a"]]
```

 

**提示：**

- `1 <= s.length <= 16`
- `s` 仅由小写英文字母组成



```c++
class Solution {
private:
    vector<vector<string>> re;
    vector<string> ans;
public:
    vector<vector<string>> partition(string s) {
        dfs(s,0);
        return re;
    }

    void dfs(string s,int i)
    {
        if(i==s.size())
        {
            re.emplace_back(ans);
            return ;
        }

        for(int j=i;j<s.size();j++)
        {
            string tmp=s.substr(i,j-i+1);
            if(hwc(tmp))
            {
                ans.emplace_back(tmp);
                dfs(s,j+1);
                ans.pop_back();
            }
        }
    }

    bool hwc(string tmp)
    {
        int left=0;
        int right=tmp.size()-1;
        while(left<=right)

        {
            if(tmp[left]!=tmp[right])
            {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
};
```

