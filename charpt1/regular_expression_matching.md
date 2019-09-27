# 10. Regular Expression Matching

## 1 题目

Given an input string (s) and a pattern (p), implement regular expression matching with support for '.' and '*'.

给一个输入字符串 s 和一个表达式 p， 实现正则匹配，支持```.``` 和```*```。 如果匹配上了返回true， 否则返回false

```
'.' Matches any single character.  '.' 匹配任何单个字符
'*' Matches zero or more of the preceding element.   '*' 匹配零个或者多个连续元素
```

The matching should cover the **entire** input string (not partial). 

匹配应该覆盖全部输入字符串（不是部分）

备注：

```
* s could be empty and contains only lowercase letters a-z.
  s 可以为空，并且只包含小写字母a-z
* p could be empty and contains only lowercase letters a-z, and characters like . or *.
  p 可以是空，并且只包含小写字母a-z 和符号 . 和 *
```

**Example1：**

```
Input:
s = "aa"
p = "a"
Output: false
Explanation: "a" does not match the entire string "aa".
```

**Example2:**

```
Input:
s = "aa"
p = "a*"
Output: true
Explanation: '*' means zero or more of the preceding element, 'a'. Therefore, by repeating 'a' once, it becomes "aa".
```

**Example3:**

```
Input:
s = "ab"
p = ".*"
Output: true
Explanation: ".*" means "zero or more (*) of any character (.)".
```

**Example4:**

```
Input:
s = "aab"
p = "c*a*b"
Output: true
Explanation: c can be repeated 0 times, a can be repeated 1 time. Therefore, it matches "aab".
```

**Example5:**

```
Input:
s = "mississippi"
p = "mis*is*p*."
Output: false
```



来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/regular-expression-matching
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。