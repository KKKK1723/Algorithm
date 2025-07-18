# 电话号码的字母组合



给定一个仅包含数字 `2-9` 的字符串，返回所有它能表示的字母组合。答案可以按 **任意顺序** 返回。

给出数字到字母的映射如下（与电话按键相同）。注意 1 不对应任何字母。

![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2021/11/09/200px-telephone-keypad2svg.png)

 

**示例 1：**

```
输入：digits = "23"
输出：["ad","ae","af","bd","be","bf","cd","ce","cf"]
```

**示例 2：**

```
输入：digits = ""
输出：[]
```

**示例 3：**

```
输入：digits = "2"
输出：["a","b","c"]
```

 

**提示：**

- `0 <= digits.length <= 4`
- `digits[i]` 是范围 `['2', '9']` 的一个数字。





```c++
class Solution {
private:
    map<char, string> p;
    vector<string> e;
public:
    vector<string> letterCombinations(string digits) {
        if (digits.empty()) return e;
        p = {
            {'2', "abc"}, {'3', "def"}, {'4', "ghi"}, {'5', "jkl"},
            {'6', "mno"}, {'7', "pqrs"}, {'8', "tuv"}, {'9', "wxyz"}
        };
        string tmp;
        dfs(tmp, digits, 0);
        return e;
    }

    void dfs(string& tmp, const string& digits, int dex) {
        if (tmp.size() == digits.size()) {
            e.push_back(tmp);
            return;
        }
        string dd = p[digits[dex]];
        for (char c : dd) {
            tmp.push_back(c);
            dfs(tmp, digits, dex + 1);
            tmp.pop_back();
        }
    }
};
```

