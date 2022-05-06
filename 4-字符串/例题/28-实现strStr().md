题目链接：[28-实现strStr()](https://leetcode-cn.com/problems/implement-strstr/)

难度：<font color="Green">简单</font>

题目内容：

实现 strStr() 函数。<br>
给你两个字符串 haystack 和 needle ，请你在 haystack 字符串中找出 needle 字符串出现的第一个位置（下标从 0 开始）。如果不存在，则返回  -1 。

说明：<br>
当 needle 是空字符串时，我们应当返回什么值呢？这是一个在面试中很好的问题。<br>
对于本题而言，当 needle 是空字符串时我们应当返回 0 。这与 C 语言的 strstr() 以及 Java 的 indexOf() 定义相符。

示例 1：<br>
输入：haystack = "hello", needle = "ll"<br>
输出：2

示例 2：<br>
输入：haystack = "aaaaa", needle = "bba"<br>
输出：-1

示例 3：<br>
输入：haystack = "", needle = ""<br>
输出：0

提示：<br>
1 <= haystack.length, needle.length <= 10^4<br>
haystack 和 needle 仅由小写英文字符组成


代码：
```
class Solution {
public:
    int strStr(string haystack, string needle) {
        int nlen = needle.length();
        int hlen = haystack.length();
        // 求next数组
        vector<int> next(nlen);
        int j = 0;
        for (int i = 1; i < nlen; ++i) {
            while (j > 0 && needle[i] != needle[j])
                j = next[j - 1];
            if (needle[i] == needle[j])
                ++j;
            next[i] = j;
        }
        // KMP匹配
        for (int nee = 0, hay = 0; nee < nlen && hay < hlen; ++hay) {
            while (nee > 0 && haystack[hay] != needle[nee])
                    nee = next[nee - 1];
            if (haystack[hay] == needle[nee]) {
                if (nee == nlen - 1)
                    return hay - nee;
                ++nee;
            }
        }
        return -1;
    }
};
```