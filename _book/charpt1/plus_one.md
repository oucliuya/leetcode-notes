# 66. Plus One

## 1. 题目

Given a non-empty array of digits representing a non-negative integer, plus one to the integer.

The digits are stored such that the most significant digit is at the head of the list, and each element in the array contain a single digit.

You may assume the integer does not contain any leading zero, except the number 0 itself.

翻译：给一个非空的数字（0~9）数组来表示一个非负的整数，给这个整数加一。数组中的数字是从左到右是高位到低位的排序，且每个元素只含一个数字。 本题假设给定的数组除了```[0]```以外不会以0开头

**Example 1:**

```
Input: [1,2,3]
Output: [1,2,4]
Explanation: The array represents the integer 123.
```

**Example 2:**

```
Input: [4,3,2,1]
Output: [4,3,2,2]
Explanation: The array represents the integer 4321.
```

链接：https://leetcode-cn.com/problems/plus-one



## 解法一

**直观解法**

"加一"之后的输出数组与输入数组的长度相等，或者前者多1。所以首先判断输入相对输入是否要增加一位。

1. 如果输出需要增加一位，那么很显然输入数组里面全是9，且输出比输入多1位，且首位为1，后面的位上全是0。
2. 如果输出不需要增加一位，那么从数组的末尾开始加一，进行"满十进一"的规则计算即可

```java
class Solution {
    public int[] plusOne(int[] digits) {
        int N = digits.length;
		boolean isMax = true;
		for (int x : digits) {
			if (x != 9) {
				isMax = false;
				break;
			}
		}
		if (isMax) {
			int[] ans = new int[N + 1];
			ans[0] = 1;
			for (int i = 1; i < N + 1; i++)
				ans[i] = 0;
			return ans;
		}
		else {
			int[] ans = new int[N];
			int add = 1;
			for(int i = N - 1; i >= 0; i--) {
				int sum = digits[i] + add;
				if (sum > 9) {
					ans[i] = sum % 10;
					add = 1;
				}
				else {
					ans[i] = sum;
					add = 0;
				}
			}
			return ans;
		}    
    }
}
```

