# 20. Valid Parentheses

## 1 题目

Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

给一个只包含 '(', ')', '{', '}', '[' and ']' 这6种字符的字符串，判断输入的字符串是否合法。

An input string is valid if:

当一下条件都满足时，输入字符串合法：

```
1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
1. 括号必须关闭
2. 括号关闭的顺序必须正确
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

## 2 解法1

用一个stack把左括号都转起来，当遇到右括号时判断它是否和栈顶的左括号是一对。如果不是，直接返回false。

如果是合法的字符串，遍历完成后，stack一定是空的。

```java
class Solution {
    public boolean isValid(String s) {
		Stack<Character> stack = new Stack<Character>();
		Map<Character,Character> map = new HashMap<Character,Character>();
		map.put(')', '(');
		map.put(']', '[');
		map.put('}', '{');
		int N = s.length();
		if (N < 1) return true;
		for (int i = 0; i < N; i++) {
			char curr = s.charAt(i);
			if (map.containsValue(curr)) {
				stack.push(curr);
			}
			if (map.containsKey(curr)) {
				if (stack.isEmpty()) return false;
				if (stack.peek() != map.get(curr)) return false;
				stack.pop();
			}
		}
		return stack.isEmpty();
	}
}
```

