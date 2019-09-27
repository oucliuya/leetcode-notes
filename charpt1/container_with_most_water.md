# 10. Container With Most Water

## 1 题目

Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

给n个非负整数 a1, a2, ..., an, 每一个整数表示一个点的坐标（i, ai）。 画n 条纵线连接点(i, ai) 和 (i, 0)。找两条线，它们和x轴一起可以组成一个容器，找出能够容纳的最多的水的量。

Note: You may not slant the container and n is at least 2.

注意：不可使容器倾斜，且n最少是2

![image](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question_11.jpg)

The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.

上图的竖线可以表示为一个数组 [1, 8, 6, 2, 5, 4, 8, 3, 7]。在这个例子中，容器能够装的最大的水面积是49.

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/container-with-most-water
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

**Example1:**

```
Input: [1,8,6,2,5,4,8,3,7]
Output: 49
```



## 解法一

