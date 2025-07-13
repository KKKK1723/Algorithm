# 括号生成





数字 `n` 代表生成括号的对数，请你设计一个函数，用于能够生成所有可能的并且 **有效的** 括号组合。

 

**示例 1：**

```
输入：n = 3
输出：["((()))","(()())","(())()","()(())","()()()"]
```

**示例 2：**

```
输入：n = 1
输出：["()"]
```

 

**提示：**

- `1 <= n <= 8`



```c++
class Solution {
private:
    vector<string>result;
public:
    vector<string> generateParenthesis(int n) {
        string now="";
        dfs(now,0,0,n);
        return result;
    }

    void dfs(string& now,int left,int right,int n)
    {
        if(now.size()==2*n)
        {
            result.emplace_back(now);
            return ;
        }

        if(left<n)
        {
            now.push_back('(');
            dfs(now,left+1,right,n);
            now.pop_back();
        }
        if(right<left)
        {
            now.push_back(')');
            dfs(now,left,right+1,n);
            now.pop_back();
        }
    }
};
```

