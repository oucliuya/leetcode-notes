# 3. longest substring without repeating characters

## 1 题目

Given a string, find the length of the longest substring without repeating characters.

**Example 1:**

```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
```

**Example 2:**

```
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

**Example 3:**

```
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
  Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

链接：https://leetcode-cn.com/problems/longest-substring-without-repeating-characters

## 2 解法一

**暴力解法：** 如果有一个函数allUnique(String s, int i, int j), 可以判断一个子字符串中的字符都是无重复的。那么我们只需要遍历所有子串，判断它是否是无重复的。找到无重复的子串中最长的一个，其长度就是答案。

### 复杂度分析

- 时间复杂度是 O(n^3)
- 空间复杂度为

```java
class Solution {
  public static int lengthOfLongestSubstring(String s) {
        int n = s.length();
        int ans = 0;
        for (int i = 0; i < n; i++)
            for (int j = i + 1; j <= n; j++)
                if (allUnique(s, i, j)) ans = Math.max(ans, j - i);
        return ans;
    }
    public static boolean allUnique(String s, int start, int end) {
        Set<Character> set = new HashSet<>();
        for (int i = start; i < end; i++) {
            Character ch = s.charAt(i);
            if (set.contains(ch)) return false;
            set.add(ch);
        }
        return true;
    }
}
```

## 3 解法二

**滑动窗口：** 用一个Hashset来作为滑动窗口。该窗口为```[i, j)``` , 将```i```、```j```初始化为0， 然后使```j```递增，判断新```j``` 位置的元素是否在set里面，如果不在，则可以继续推进```j``` ，从而获得更长的无重复子串；如果```j``` 位置的元素在set里面，则说明当前的不重复子串已经到头了，那么可以将```i```位置的元素从set里面删掉，并将```i``` 向右推进1位。

比起暴力法，滑动窗口能够减少判断次数。两种方法都轮询了```n*(n-1)```个子串， 但是前者对于每个子串都要判断是否有重复值，要判断```j - i```次；而后者对于每个子串只做了1次判断。本方法的时间复杂度为 ```O(n^2)```

**注：**  Hashset 是无序集合，包含不重复的元素。HashSet可以实现Set 接口

``` java
class Solution {
  public static int lengthOfLongestSubstring(String s) {
		int n = s.length();
		Set<Character> set = new HashSet();
		int i = 0, j=0, ans = 0;
		while (i < n && j < n) {
			if (!set.contains(s.charAt(j))) {
				set.add(s.charAt(j++));
				ans = Math.max(ans, j - i);
			}
			else {
				set.remove(s.charAt(i++));
			}
		}
		return ans;
    }
}
```



## 3 解法三

**优化的滑动窗口：** 改进点是当我们发现了```j```位置的元素与窗口```[i, j)``` 中的```k```位置的值相同时，我们可以直接把```[i, k]```这一段窗口丢弃掉，将新窗口设为```[k+1, j)``` 并继续推进```j```，而不需要慢慢地使```i```递增。

这种办法需要通过```j```位置的值来找窗口中相同值的位置```k```, 这时候```HashSet```就不够用了，需要使用```HashMap```来存储字符的值和位置序号。 Map的key 为字符的值，value为字符在```String s``` 中的位置序号。

步骤：

1. ``i, j`` 的初始值都设为0
2.  如果窗口map的key里面含有```j```位置的值，则获得这个值对应的values， 即```k+ 1```。 这时窗口的起点```i```应当设为k + 1
3.  答案即为 ```ans```与 ``` j - i + 1``` 中的较大值 
4.  map 填入 ```k-v```对 ```s[j], j+1```

上述循环有一个问题，map中的位置值比s中的位置值大1， 而非相等。为什么？

### 复杂度分析

- 方法二 对 s 字符串中每个字符遍历了两次， （```i```, ```j``` 各自遍历了一次），其复杂度实际是```O(2n)```
- 方法三 对 s 字符串的每个字符遍历了1次，（```j``` 遍历了一次）， 其复杂度为```O(2n)```

``` java
class Solution {
  public static int lengthOfLongestSubstring(String s) {
    int n = s.length();
		int ans = 0;
		Map<Character, Integer> map = new HashMap<>();
		for (int i = 0, j = 0; j < n; j++) {
			if (map.containsKey(s.charAt(j))) {
				i = Math.max(map.get(s.charAt(j)), i);
			}
			ans = Math.max(ans, j - i + 1);
			map.put(s.charAt(j), j + 1);
		}
		return ans;
    }
}
```

