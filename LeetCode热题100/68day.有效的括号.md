# 有效的括号





给定一个只包括 `'('`，`')'`，`'{'`，`'}'`，`'['`，`']'` 的字符串 `s` ，判断字符串是否有效。

有效字符串需满足：

1. 左括号必须用相同类型的右括号闭合。
2. 左括号必须以正确的顺序闭合。
3. 每个右括号都有一个对应的相同类型的左括号。

 

**示例 1：**

**输入：**s = "()"

**输出：**true

**示例 2：**

**输入：**s = "()[]{}"

**输出：**true

**示例 3：**

**输入：**s = "(]"

**输出：**false

**示例 4：**

**输入：**s = "([])"

**输出：**true

**示例 5：**

**输入：**s = "([)]"

**输出：**false

 

**提示：**

- `1 <= s.length <= 104`
- `s` 仅由括号 `'()[]{}'` 组成



```c++
class Solution {
public:
    bool isValid(string s) {
        deque<char>dq;
        for(auto &it:s)
        {
            if(it=='('||it=='{'||it=='[')
            {
                dq.push_back(it);
            }
            else
            {
                if(dq.empty())return false;
                char tmp=dq.back();
                if((tmp=='('&&it!=')')||(tmp=='{'&&it!='}')||(tmp=='['&&it!=']'))
                {
                    return false;
                }
                dq.pop_back();
            }
        }
        if(dq.size())return false;
        return true;
    }
};
```

