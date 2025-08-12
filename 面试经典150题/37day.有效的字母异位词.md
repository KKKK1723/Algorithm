# 有效的字母异位词



给定两个字符串 `s` 和 `t` ，编写一个函数来判断 `t` 是否是 `s` 的 字母异位词。

 

**示例 1:**

```
输入: s = "anagram", t = "nagaram"
输出: true
```

**示例 2:**

```
输入: s = "rat", t = "car"
输出: false
```

 

**提示:**

- `1 <= s.length, t.length <= 5 * 104`
- `s` 和 `t` 仅包含小写字母

 





```c++
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.size()!=t.size())return false;
        
        unordered_map<char,int>mp;
        unordered_map<char,int>mpp;
        for(auto& c:t)
        {
            mp[c]++;
        }

        for(auto& c:s)
        {
            mpp[c]++;
        }

        for(auto& c:mpp)
        {
            if(mpp[c.first]!=mp[c.first])return false;
        }
        return true;
    }
};
```

