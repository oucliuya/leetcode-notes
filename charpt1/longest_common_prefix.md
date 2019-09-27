# 14. Longest Common Prefix

## 题目

Write a function to find the longest common prefix string amongst an array of strings.If there is no common prefix, return an empty string "".

写一个函数，找到一组字符串的最长的公共前缀。如果没有公共的前缀，则返回空字符串""

Example1:

```
Input: ["flower","flow","flight"]
Output: "fl"
```

Example2:

```
Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

**Note:**

All given inputs are in lowercase letters `a-z`.

输入的字符串中的字符都是小写的a-z

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/longest-common-prefix
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解法一



```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        int N = strs.length;
        if (N == 0)
            return "";
        String res = strs[0];
        for (int i = 1; i < N; i++)
        {
            res = commonString(res, strs[i]);
            // System.out.println(res+' '+res.length());
        }
        return res;
    }
    public static String commonString(String a, String b){
        String res = a.length() > b.length() ? b : a;
        for (int i = 0; i < res.length(); i++){
            if (a.charAt(i) != b.charAt(i))
                res = res.substring(0, i);
        }
        return res;
    }
}
```

