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
1. [LC 33 Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/submissions/)
  
    Similar to the regular binary search, the idea of solving this problem is keep narrowing down the range where the target could exist. However, we can't simply eliminate half of the elements by just comparing target and nums[mid] every time since the entire array is neither sorted in ascending order nor in descending order after rotating. 
    
    But we can still use monotone intervals to narrow down the range where the target could be. 
    - If nums[mid] >= nums[left] then [left, mid] is a monotone interval in which all the elements are sorted in ascending order. In this case, if target is within range [left, mid) then we narrow down search range to [left,mid-1], otherwise we narrow down search range to [mid+1, right]. 
    - If nums[mid] < nums[left] then [mid, right] is a montone interval in which all the elements are sorted in ascending order. In this case, if target is within range (mid,right] then we narrow down search range to [mid+1,right], otherwise we narrow down search range to [left,mid-1].

<img src="https://github.com/idanhuang/idanhuang.github.io/blob/master/image/rotated_sorted_array_4.png" data-canonical-src="https://github.com/idanhuang/idanhuang.github.io/blob/master/image/rotated_sorted_array_4.png" width="480" height="200" />
  
- LC 81 Search in Rotated Sorted Array II
- LC 153 Find Minimum in Rotated Sorted Array
- LC 154 Find Minimum in Rotated Sorted Array II
