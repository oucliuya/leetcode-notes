# 1. Two Sum

## 1 题目

Given an array of integers, return indices of the two numbers such that they add up to a specific target.You may assume that each input would have exactly one solution, and you may not use the same element twice.

**翻译**给定一个整数数组和一个目标整数，找出这个数组中两个和为目标整数的元素，输出它们的位置。你可以假设每个输入刚好有一个答案，并且不能两次使用同一个元素。

**Example:**

```python
Given nums = [2, 7, 11, 15], target = 9,
Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

## 2 解法一

直观思路：使用一个HashMap 存储所有的元素的```值-位置```的key-value对。遍历输入数组nums中的每个元素，算出它被target减的差值，如果差值也在map中，而且与该元素的位置不同，则返回该元素的位置和差值的位置；否则就把这个元素的```值-位置```加入到map中

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length ; i++){
            int dvalue = target - nums[i];
            if (map.containsKey(dvalue) && i != map.get(dvalue)){
                return new int[] {i,map.get(dvalue)};
            }
            map.put(nums[i], i);
        }
        throw new IllegalArgumentException("No solution");
    }
}
```



