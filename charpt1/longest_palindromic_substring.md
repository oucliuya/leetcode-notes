# 5. Longest Palindromic Substring

## 1 题目

Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

给定一个字符串s，找到s中最长的回文子串。可以假设s的最大长度使1000。 

**Example 1**

```
Input: "babad"
Output: "bab"
Note: "aba" is also a valid answer.
```

**Example 2**

```
Input: "cbbd"
Output: "bb"
```



来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/longest-palindromic-substring

## 2 解法一 ：暴力法

列举所有的子串，判断是不是回文串，返回最长的。 这种方式容易超过时间限制。

时间复杂度为```O(n^3)```

```java
class Solution {
    public String longestPalindrome(String s) {
        int n = s.length();
		String ans = new String();
		for (int i = 0; i < n; i++)
			for (int j = i + 1; j <= n; j++) {
				String sub = s.substring(i, j);
				if (isPalindrome(sub))
					if (sub.length() > ans.length()) ans = sub;			
			}
		return ans;			
    }
   public boolean isPalindrome(String s) {
		int n = s.length();
		for (int i = 0, j = n-1; i <= j; i++, j--) {
			if (s.charAt(i) != s.charAt(j)) return false;
		}
		return true;
	}
}
```



## 3 解法二： 动态规划

```java
class Solution {
    public String longestPalindrome(String s) {
        
    }
}
```



