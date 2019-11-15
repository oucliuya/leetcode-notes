# 42. Trapping Rain Water

## 1 题目

Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it is able to trap after raining.

给n个非负的整数来代表高度，每个条形的宽度都是1。计算这些柱子之间能够存多少水（蓝色部分的面积）

![image](https://assets.leetcode.com/uploads/2018/10/22/rainwatertrap.png)

The above elevation map is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped. Thanks Marcos for contributing this image!

**Example1：**

```
Input: [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/trapping-rain-water
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。



## 2 解法一

暴力法：遍历每一块，

1. 求该块左边最大值（包括该块）max_left
2. 求该块右边最大值 （包括该块）max_right
3. ans += min( max_left, max_right) - heigt[i]

```
class Solution {
    public int trap(int[] height) {
		
		int size = height.length;
		int ans = 0;
		for (int i = 1; i < size-1; i++) {
            int max_left = 0, max_right = 0;
			for (int j = i; j >= 0; j--) {
				max_left = Math.max(max_left, height[j]);
			}
			for (int j = i; j < size; j++) {
				max_right = Math.max(max_right, height[j]);
			}
			
			ans += Math.min(max_left, max_right) - height[i];
		}
		return ans;
    }
}
```

