# P1091 [NOIP 2004 提高组] 合唱队形

## 题目描述

$n$ 位同学站成一排，音乐老师要请其中的 $n-k$ 位同学出列，使得剩下的 $k$ 位同学排成合唱队形。

合唱队形是指这样的一种队形：设 $k$ 位同学从左到右依次编号为 $1,2,$ … $,k$，他们的身高分别为 $t_1,t_2,$ … $,t_k$，则他们的身高满足 $t_1< \cdots <t_i>t_{i+1}>$ … $>t_k(1\le i\le k)$。

你的任务是，已知所有 $n$ 位同学的身高，计算最少需要几位同学出列，可以使得剩下的同学排成合唱队形。

## 输入格式

共二行。

第一行是一个整数 $n$（$2\le n\le100$），表示同学的总数。

第二行有 $n$ 个整数，用空格分隔，第 $i$ 个整数 $t_i$（$130\le t_i\le230$）是第 $i$ 位同学的身高（厘米）。

## 输出格式

一个整数，最少需要几位同学出列。

## 输入输出样例 #1

### 输入 #1

```
8
186 186 150 200 160 130 197 220
```

### 输出 #1

```
4
```

## 说明/提示

对于 $50\%$ 的数据，保证有 $n \le 20$。

对于全部的数据，保证有 $n \le 100$。

AC代码
```
#include <iostream>
#include <vector>
#include <algorithm>
#include<cstring>
using namespace std;
typedef long long ll;
const ll N = 200;
ll n, a[N];
ll maxlen = -1e8;
void slove()
{
    cin >> n;
    for (int i = 0; i <n; i++)
    {
        cin >> a[i];
    }

    for (int i = 0; i < n; i++) // 中间坐标
    {
        int dex = 0;
        int q[N]; // 辅助数组
        memset(q,0, sizeof(q));
        q[0] = a[0];
        ll lenleft = 0;
        for (int j = 1; j <= i; j++) // 找左侧的最长递增子序列
        {
            if (a[j] > q[dex])
            {
                dex++;         // 下一位放这
                q[dex] = a[j]; // 直接放进来
                // 此时q数组中有dex位数
            }
            else if (a[j] < q[dex])
            {
                // 找到第一个大于a[i]的元素 进行替换
                int pos = lower_bound(q, q + 1 + dex, a[j]) - q;
                q[pos] = a[j];
               
            }
        }
        lenleft = dex+1;

        ll res = 0;
        int p[N];    // 辅助数组
        memset(p, 0, sizeof(p));
        p[0] = a[n-1]; // 从最后一位开始
        ll lenright = 0;
        for (int j = n - 2; j >= i; j--) // 找右侧的最长递增子序列
        {
            if (a[j] > p[res])
            {
                res++;
                p[res] = a[j];
            }
            else if (a[j] < p[res])
            {
                int pos = lower_bound(p , p + 1 + res, a[j]) - p;
                p[pos] = a[j];
            }
        }
        lenright = res+1;

        maxlen = max(lenright + lenleft - 1, maxlen);
    }

    cout << n-maxlen;
}

signed main()
{
    ios::sync_with_stdio(0);
    cin.tie(0);
    cout.tie(0);
    slove();
    return 0;
}
```

思路分析在CSDN  https://blog.csdn.net/2401_87117051?spm=1010.2135.3001.5343
