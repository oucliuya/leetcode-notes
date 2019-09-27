# 12. Integer to Roman

## 1 题目

Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

罗马数字由7个不同的符号的组合来表示：I, V, X, L, C, D, M

```
Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```

For example, two is written as II in Roman numeral, just two one's added together. Twelve is written as, XII, which is simply X + II. The number twenty seven is written as XXVII, which is XX + V + II.

例如，2 写成罗马数字是 II, 是两个1相加； 12 写成XII， 是```X + II```；27 写成```XXVII```, 是```XX + V + II```。

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

罗马数字通常是大数排在左边，小数排在右边。但是，数字4并不写作```IIII```, 而是写成```IV```。因为```I```在```V```前面，所以要用5减去1得到4。同样的规律也运用在数字9，写作```IX```。做减法的情况一共有6种，如下：

```
I can be placed before V (5) and X (10) to make 4 and 9. 
I 可以放在V(5) 和 X(10) 的前面，组成4和9
X can be placed before L (50) and C (100) to make 40 and 90. 
X 可以放在L(50)和C(100) 的前面， 组成40和90
C can be placed before D (500) and M (1000) to make 400 and 900.
C 可以放在D(500)和M(1000) 的前面，组成400 和 900
```

Given an integer, convert it to a roman numeral. Input is guaranteed to be within the range from 1 to 3999.

给出一个整数，把它转化成一个罗马数字。输入的整数在范围 ```[1，3999]```之内

**Example1:**

```
Input: 3
Output: "III"
```

**Example2:**

```
Input: 4
Output: "IV"
```

**Example3:**

```
Input: 9
Output: "IX"
```

**Example4:**

```
Input: 58
Output: "LVIII"
Explanation: L = 50, V = 5, III = 3.
```

**Example5:**

```
Input: 1994
Output: "MCMXCIV"
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```



来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/integer-to-roman
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

