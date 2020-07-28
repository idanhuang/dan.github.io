# Rotated Sorted Array

## What is rotated sorted array
An array is sorted in ascending order and rotated at some unknown pivots.
![image](https://github.com/idanhuang/idanhuang.github.io/blob/master/image/roated_sorted_array_1.png)

## Properties
1. The left interval and right interval of the inflection point (red line shown as below) are both sorted in ascending order.
![image](https://github.com/idanhuang/idanhuang.github.io/blob/master/image/roated_sorted_array_2.png)
2. Minimal value of left interval is greater than maximum value of right interval.
![image](https://github.com/idanhuang/idanhuang.github.io/blob/master/image/roated_sorted_array_3.png)


## Problems
1. [LC 33 Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/submissions/)
  
    Similar to the regular binary search, the idea of solving this problem is keep narrowing down the range where the target could exist. However, we can't eliminate half of the elements by just comparing target and nums[mid] every time since the entire array is neither in ascending order nor in descending order after rotating. 
    
    But we can still use monotone intervals to narrow down the range where the target could be. Everytime we check whether the target is within a monotone interval and then narrow down the search range.
    - If nums[mid] >= nums[left] then [left, mid] is a monotone interval in which all the elements are sorted in ascending order. In this case, if target is within range [left, mid) then we narrow down search range to [left,mid-1], otherwise we narrow down search range to [mid+1, right]. 
    - If nums[mid] < nums[left] then [mid, right] is a montone interval in which all the elements are sorted in ascending order. In this case, if target is within range (mid,right] then we narrow down search range to [mid+1,right], otherwise we narrow down search range to [left,mid-1].

   <img src="https://github.com/idanhuang/idanhuang.github.io/blob/master/image/rotated_sorted_array_4.png" data-canonical-src="https://github.com/idanhuang/idanhuang.github.io/blob/master/image/rotated_sorted_array_4.png" width="460" height="200" />
  
  ```C#
  public class Solution {
    public int Search(int[] nums, int target) {
        
        if(nums == null || nums.Length == 0)
            return -1;
        
        int left = 0, right = nums.Length - 1;
        
        while(left <= right)
        {
            int mid = left + (right - left) / 2;
            
            if(target == nums[mid])
            {
                return mid;
            }
            else if(nums[mid] >= nums[left])
            {
                if(target >= nums[left] && target < nums[mid])
                    right = mid - 1;
                else
                    left = mid + 1;
            }
            else
            {
                if(target > nums[mid] && target <= nums[right])
                    left = mid + 1;
                else
                    right = mid - 1;
            }
        }
        
        return -1;
    }
}
  ```
2. [LC 81 Search in Rotated Sorted Array II](https://leetcode.com/problems/search-in-rotated-sorted-array-ii)
- LC 153 Find Minimum in Rotated Sorted Array
- LC 154 Find Minimum in Rotated Sorted Array II
