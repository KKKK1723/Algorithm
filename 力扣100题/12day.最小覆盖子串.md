# 76. 最小覆盖子串

**难度：困难**

## 题目描述

给你一个字符串 `s` 、一个字符串 `t`。返回 `s` 中涵盖 `t` 所有字符的最小子串。如果 `s` 中不存在涵盖 `t` 所有字符的子串，则返回空字符串 ""。

**注意：**

- 对于 `t` 中重复字符，我们寻找的子字符串中该字符数量必须不少于 `t` 中该字符数量。
- 如果 `s` 中存在这样的子串，我们保证它是唯一的答案。

---

## 示例

**示例 1：**
```
输入：s = "ADOBECODEBANC", t = "ABC"
输出："BANC"
解释：最小覆盖子串 "BANC" 包含来自字符串 t 的 'A'、'B' 和 'C'。
```

**示例 2：**
```
输入：s = "a", t = "a"
输出："a"
解释：整个字符串 s 是最小覆盖子串。
```

**示例 3：**
```
输入: s = "a", t = "aa"
输出: ""
解释: t 中两个字符 'a' 均应包含在 s 的子串中，因此没有符合条件的子字符串，返回空字符串。
```

---

## 提示

- m == s.length
- n == t.length
- 1 <= m, n <= 10^5
- s 和 t 由英文字母组成

---


```
class Solution {
public:
    unordered_map <char, int> ori, cnt;

    bool check() {
        for (const auto &p: ori) {
            if (cnt[p.first] < p.second) {
                return false;
            }
        }
        return true;
    }

    string minWindow(string s, string t) {
        for (const auto &c: t) {
            ++ori[c];
        }

        int l = 0, r = -1;
        int len = INT_MAX, ansL = -1, ansR = -1;

        while (r < int(s.size())) {
            if (ori.find(s[++r]) != ori.end()) {
                ++cnt[s[r]];
            }
            while (check() && l <= r) {
                if (r - l + 1 < len) {
                    len = r - l + 1;
                    ansL = l;
                }
                if (ori.find(s[l]) != ori.end()) {
                    --cnt[s[l]];
                }
                ++l;
            }
        }

        return ansL == -1 ? string() : s.substr(ansL, len);
    }
};


```
