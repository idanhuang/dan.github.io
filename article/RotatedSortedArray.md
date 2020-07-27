# Rotated Sorted Array

## What is rotated sorted array
An array is sorted in ascending order and rotated at some unknown pivots.
![image](https://github.com/idanhuang/idanhuang.github.io/blob/master/image/roated_sorted_array_1.png)

## Properties
1. The left part and right part of the inflection point (red line shown as below) are both sorted in ascending order.
![image](https://github.com/idanhuang/idanhuang.github.io/blob/master/image/roated_sorted_array_2.png)

2. Minimal value of left part is greater than maximum value of right part.
![image](https://github.com/idanhuang/idanhuang.github.io/blob/master/image/roated_sorted_array_3.png)


## Problems
- [LC 33 Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/submissions/)
  
Similar to the regular binary search, the idea is to keep narrowing down the range where the target value could exist. However, the entire array is neither sorted in ascending order nor in descending order since the array is rotated at a unknown pivot, thus we can't simply eliminate half part by comparing target and nums[mid] every time. But we can narrow down range by comparing nums[mid] and nums[left]

![image](https://github.com/idanhuang/idanhuang.github.io/blob/master/image/rotated_sorted_array_4.png)
  
- LC 81 Search in Rotated Sorted Array II
- LC 153 Find Minimum in Rotated Sorted Array
- LC 154 Find Minimum in Rotated Sorted Array II
