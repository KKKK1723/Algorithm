# 最长公共前缀



编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 `""`。

 

**示例 1：**

```
输入：strs = ["flower","flow","flight"]
输出："fl"
```

**示例 2：**

```
输入：strs = ["dog","racecar","car"]
输出：""
解释：输入不存在公共前缀。
```

 

**提示：**

- `1 <= strs.length <= 200`
- `0 <= strs[i].length <= 200`
- `strs[i]` 如果非空，则仅由小写英文字母组成



```c++
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if(strs.size()==1&&strs[0].size()==0)return "";

        string tmp=strs[0];
        for(int i=1;i<strs.size();i++)
        {
            tmp=bl(tmp,strs[i]);
            if(tmp.size()==0)return "";
        }
        return tmp;
    }

    string bl(string s1,string s2)
    {
        int length=min(s1.size(),s2.size());
        int dex=0;
        for(int i=0;i<length;i++)
        {
            if(s1[i]==s2[i])dex++;
            else
            {
                break;
            }
        }
        s1=s1.substr(0,dex);
        return s1;
    }
};
```

