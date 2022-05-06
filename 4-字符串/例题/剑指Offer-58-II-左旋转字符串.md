题目链接：[剑指Offer 58-II-左旋转字符串](https://leetcode-cn.com/problems/zuo-xuan-zhuan-zi-fu-chuan-lcof/)

难度：<font color="Green">简单</font>

题目内容：

字符串的左旋转操作是把字符串前面的若干个字符转移到字符串的尾部。请定义一个函数实现字符串左旋转操作的功能。比如，输入字符串"abcdefg"和数字2，该函数将返回左旋转两位得到的结果"cdefgab"。

示例 1：<br>
输入: s = "abcdefg", k = 2<br>
输出: "cdefgab"

示例 2：<br>
输入: s = "lrloseumgh", k = 6<br>
输出: "umghlrlose"

限制：<br>
1 <= k < s.length <= 10000


代码：
```
class Solution {
public:
    string reverseLeftWords(string s, int n) {
        int len = s.length();
        for (int start = 0, end = len - 1; start < end; ++start, --end)
            swap(s[start], s[end]);
        for (int start = 0, end = len - 1 - n; start < end; ++start, --end)
            swap(s[start], s[end]);
        for (int start = len - n, end = len - 1; start < end; ++start, --end)
            swap(s[start], s[end]);
        return s;
    }
};
```