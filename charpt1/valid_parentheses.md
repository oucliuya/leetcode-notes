# 20. Valid Parentheses

## 1 题目

Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

```
1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
```

Note that an empty string is also considered valid.

**Example1:**

```
Input: "()"
Output: true
```

**Example2:**

```
Input: "()[]{}"
Output: true
```

**Example3:**

```
Input: "(]"
Output: false
```

**Example4:**

```
Input: "([)]"
Output: false
```

**Example5:**

```
Input: "{[]}"
Output: true
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/valid-parentheses
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。