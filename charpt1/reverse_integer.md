# 7. Reverse Integer

## 1 题目

Given a 32-bit signed integer, reverse digits of an integer.

给定一个32比特的有符号整数，翻转数字

**Example1:**

```
Input: 123
Output: 321
```

**Example2:**

```
Input: -123
Output: -321
```

**Example3:**

```
Input: 120
Output: 21
```

**Note:**
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−2^31,  2^31 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

注意：假设我们的环境只能存储32bit位以内的整数:[−2^31,  2^31 − 1]。对于本题目，如果翻转的数字超过了范围，则返回0.

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/reverse-integer

## 2 解法一

**弹出和压入数字&溢出前检查：** ``` x % 10``` 可以把最右边一位弹出来。 我们可以用一个变量pop来存储右侧弹出的数字，用一个r来存储返回值。每次从x的最右侧弹出一值存入pop中，再把pop 压入到 r 中。 停止条件是 x 为 0，关键是要检查r是否越界。

如果 r 是正数，当 ``` r > Integer.MAX_VALUE /10 ``` 时，下一次执行压入操作 ``` r = r * 10 + pop``` 时，r 必然越界；当``` r == Integer.MAX_VALUE/10 = 2147483647/10 = 2147483640``` 时，下次执行压入操作是否越界取决于 pop 的大小， 如果 ``` pop > 7 ```, 则  ``` r = r * 10 + pop``` 必然越界。

如果r 是负数， 当 ``` r < Integer.MIN_VALUE / 10``` 时，下一次执行压入操作必然越界； 当``` r = Integer.MIN_VALUE / 10 = -2147483648 / 10  = - 2147483640``` 时， 下次执行压入操作是否越界取决于pop的大小，如果 ```pop < -8 ```, 则下次压入必然越界。

```java
class Solution {
    public int reverse(int x) {
        int r = 0, pop = 0;
        while (x != 0){
            if (r > Integer.MAX_VALUE / 10 || (r == Integer.MAX_VALUE / 10 && pop > 7)){
                return 0;
            }
            if (r < Integer.MIN_VALUE / 10 || (r == Integer.MIN_VALUE / 10 && pop < -8)){
                return 0;
            }
            pop = x % 10;
            x /= 10;
            r = r * 10 + pop;
        }
        return r;
    }
}
```

