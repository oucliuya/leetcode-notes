# 13. Roman to Integer

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

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

```
I can be placed before V (5) and X (10) to make 4 and 9. 
X can be placed before L (50) and C (100) to make 40 and 90. 
C can be placed before D (500) and M (1000) to make 400 and 900.
```

Given a roman numeral, convert it to an integer. Input is guaranteed to be within the range from 1 to 3999.

Example1:

```
Input: "III"
Output: 3
```

Example2:

```
Input: "IV"
Output: 4
```

Example3:

```
Input: "IX"
Output: 9
```

Example4:

```
Input: "LVIII"
Output: 58
Explanation: L = 50, V= 5, III = 3.
```

Example5:

```
Input: "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```



来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/roman-to-integer
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解法一

**直观方法：**用一个hashMap把罗马字符跟对应的数字以k-v对的方式存储下来。遍历整个罗马字符串，如果第 i 个字符比第 i+1 个字符小，说明要用减法模式，反之用加法模式。

```java
class Solution {
    public int romanToInt(String s) {
        int res = 0;
        int N = s.length();
        HashMap<Character, Integer> a = new HashMap<Character, Integer>();
        a.put('I', 1);
        a.put('V', 5);
        a.put('X', 10);
        a.put('L', 50);
        a.put('C', 100);
        a.put('D', 500);
        a.put('M', 1000);
        for (int i = 0; i < N - 1; i++){
            // System.out.println(a.get(s.charAt(i)));
            if (a.get(s.charAt(i)) < a.get(s.charAt(i+1))) 
                res -= a.get(s.charAt(i));
            else
                res += a.get(s.charAt(i));
        }
        return res + a.get(s.charAt(N-1));
    }
}
```

