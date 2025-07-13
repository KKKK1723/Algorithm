# 单词搜索





给定一个 `m x n` 二维字符网格 `board` 和一个字符串单词 `word` 。如果 `word` 存在于网格中，返回 `true` ；否则，返回 `false` 。

单词必须按照字母顺序，通过相邻的单元格内的字母构成，其中“相邻”单元格是那些水平相邻或垂直相邻的单元格。同一个单元格内的字母不允许被重复使用。

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2020/11/04/word2.jpg)

```
输入：board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
输出：true
```

**示例 2：**

![img](https://assets.leetcode.com/uploads/2020/11/04/word-1.jpg)

```
输入：board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "SEE"
输出：true
```

**示例 3：**

![img](https://assets.leetcode.com/uploads/2020/10/15/word3.jpg)

```
输入：board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCB"
输出：false
```

 

**提示：**

- `m == board.length`
- `n = board[i].length`
- `1 <= m, n <= 6`
- `1 <= word.length <= 15`
- `board` 和 `word` 仅由大小写英文字母组成

 

```c++
class Solution {
private:
    bool found;
    int dx[4] = {-1, 1, 0, 0};
    int dy[4] = {0, 0, -1, 1};
    
public:
    bool exist(vector<vector<char>>& board, string word) {
        if (word.empty()) return true;
        if (board.empty() || board[0].empty()) return false;
        
        found = false;
        int m = board.size(), n = board[0].size();
        
        for (int i = 0; i < m && !found; i++) {
            for (int j = 0; j < n && !found; j++) {
                if (board[i][j] == word[0]) {
                    dfs(board, word, i, j, 0);
                }
            }
        }
        return found;
    }
    
private:
    void dfs(vector<vector<char>>& board, const string& word, int x, int y, int index) {
        if (index == word.length()) {
            found = true;
            return;
        }
        
        if (x < 0 || x >= board.size() || y < 0 || y >= board[0].size()) {
            return;
        }

        if (board[x][y] != word[index]) {
            return;
        }
        
        
        char temp = board[x][y];
        board[x][y] = '#';
        
        for (int i = 0; i < 4 && !found; i++) {
            int nx = x + dx[i];
            int ny = y + dy[i];
            dfs(board, word, nx, ny, index + 1);
        }
        
        board[x][y] = temp;
    }
};
```

