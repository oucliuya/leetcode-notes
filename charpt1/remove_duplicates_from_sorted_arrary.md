# 26. Remove Duplicates From Sorted Array

## 1 题目

Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.

输入一个已经排好序的数字型数组，删除其中的重复元素，使得每个元素只出现一次。返回新数组的长度。

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

不要创建另外一个数组，你只能在输入的数组中操作。当然，你可以额外使用 O(1)的空间

**Example1:**

```
Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.

It doesn't matter what you leave beyond the returned length.
```

**Example2:**

```
Given nums = [0,0,1,1,1,2,2,3,3,4],

Your function should return length = 5, with the first five elements of nums being modified to 0, 1, 2, 3, and 4 respectively.

It doesn't matter what values are set beyond the returned length.
```

Clarification:

Confused why the returned value is an integer but your answer is an array?

为什么你要返回一个整数而不是一个数组呢？

Note that the input array is passed in by reference, which means modification to the input array will be known to the caller as well. 注意，输入的数组是以引用的方式传入的，这意味着修改输入的数组也会被调用者察觉，所以你返回一个数组就够了。

Internally you can think of this:

```
// nums is passed in by reference. (i.e., without making a copy)
int len = removeDuplicates(nums);

// any modification to nums in your function would be known by the caller.
// using the length returned by your function, it prints the first len elements.
for (int i = 0; i < len; i++) {
    print(nums[i]);
}
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。



## 2 题解

这个题目适合使用快慢指针。i 是慢指针，j是快指针， 每当发现```num[i]==num[j]```， 就把j往前推，让它跳过重复项。直到 ```num[i] != num[j]```， 这时就应该让i往前进一步，并把num[j]复制到num[i]

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int i = 0;
        for(int j = 0; j < nums.length; j++){
            if( nums[i] != nums[j]){
                i++;
                nums[i] = nums[j];
            }
        }
        return i + 1;
    }
}
```

