题目链接：[剑指Offer 05-替换空格](https://leetcode-cn.com/problems/ti-huan-kong-ge-lcof/)

难度：<font color="Green">简单</font>

题目内容：

请实现一个函数，把字符串 s 中的每个空格替换成"%20"。

示例 1：<br>
输入：s = "We are happy."<br>
输出："We%20are%20happy."

限制：<br>
0 <= s 的长度 <= 10000


代码：
```
class Solution {
public:
    string replaceSpace(string s) {
        int count = 0;
        int j = s.length() - 1;
        for (auto c: s) {
            if (c == ' ')
                ++count;
        }
        s.resize(j + 1 + 2 * count, ' ');
        int i = s.length() - 1;
        while (i > j) {
            if (s[j] == ' ') {
                s[i] = '0';
                s[i - 1] = '2';
                s[i - 2] = '%';
                i -= 3;
            }
            else {
                s[i--] = s[j];
            }
            --j;
        }
        return s;
    }
};
```