# 9. Palindrome Number

## 1 题目

Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

判断一个整数是否是回文数。 一个回文数是指它从前往后读或者从后往前读是一样的

**Example1:**

```
Input: 121
Output: true
```

**Example2:**

```
Input: -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```

**Example3:**

```
Input: 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```

**Follow up:**

Coud you solve it without converting the integer to a string?

能否不把整数转为字符串来解该题？

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/palindrome-number
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 2 解法一

借鉴第7题的方法。

如果输入值x为负数，它必然不是回文数。

当x为正数时，使用**弹出和压入数字&溢出前检查**的方法将x翻转，如果x翻转之后跟翻转之前相等则是回文数，否则不是回文数。

本方法的复杂度是```O(N)```

```java
class Solution {
	public static boolean isPalindrome(int x) {
		int pop = 0, rev = 0, old = x;
        if (x < 0) 
            return false;
        else{
            while(x != 0){
                if (rev > Integer.MAX_VALUE || rev == Integer.MAX_VALUE && pop > 7){
                    return false;
                }
                pop = x % 10;
                rev = rev * 10 + pop;
                x /= 10;
            }
        }
        if (old == rev)
            return true;
        return false;
	}  
}
```



## 3 解法二

如果 x<0 ,必然为false。如果 ```x % 10 == 0``` , 即x是10的倍数，那么x必须为0才有可能是回文数。

当 x>0 时， 同样是使用弹出和压入数字的方法获取得从右向左读的反转数字 rev， 我们不需要把 x完全翻转，只需要翻转一半（故临界条件是rev < x）。 因为一个回文数的前一半和后一半是镜像对称的。如果回文数x的位数是偶数，那么while循环退出后x与rev应该是相等的； 如果回文数x 的位数是基数，如```12321```, 那么while循环退出后 x=12， rev=123， 我们可以去除掉对称轴```3```, 再来比较x 与 rev， 应该满足 ``` x = rev/10```。

本方法的循环只需执行 N/2 次， 是上一种的一半。

```java
public static boolean isPalindrome(int x) { 
        if (x < 0 || x % 10 == 0 && x != 0){
            return false;
        }
        int rev = 0;
        while (rev < x){
            rev = rev * 10 + x % 10;
            x /= 10;
            System.out.println(x+" "+rev);
        }
        System.out.println(x+" "+rev);
        return rev == x || x == rev / 10; 
    }
```



