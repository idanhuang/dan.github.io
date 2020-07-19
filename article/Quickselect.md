# Quickselect
Quickselect is a selection algorithm to find the Kth smallest/largest element in an unsorted list. Quickselect uses the same overall approach as Quicksort, choosing one element as the pivot and then partition the elements in two based on the pivot (every element on the left is less than the pivot and evey element on the right is greater than the pivot). 

## Time complextiy
Like Quicksort, Quickselect is fast in practice but has poor worst-case performance. The worst-case time complexity is O(n^2), the average and best case time complexity is O(n).

- Worst-case <br/>
Each partitioning only excludes one elements, so the time complexity is n + (n-1) + (n-2) + ... + 2 + 1 = n*(n+1)/2, which is O(n^2). 
- Average case <br/>
Each partitioning excludes half of all the elements, so the time complexity is n + n/2 + n/4 + ... + 1 = 2n*[1-(1/2)^n] < 2n, which is O(n).

## FindKthSmallest
```C#
using System;

public class Solution
{
    public int FindKthSmallest(int[] nums, int k)
    {
        if (nums == null || nums.Length == 0 || nums.Length < k)
            return Int32.MinValue;

        int left = 0, right = nums.Length - 1;
        int pivotIndex = 0;
        while (left < right)
        {
            pivotIndex = Partition(nums, left, right);

            if (pivotIndex == k - 1)
                break;
            else if (pivotIndex < k - 1)
                left = pivotIndex + 1;
            else
                right = pivotIndex - 1;
        }

        return nums[pivotIndex];
    }

    public int Partition(int[] nums, int left, int right)
    {
        int pivot = nums[right];
        int pivotIndex = left;
        for(int i = left; i < right; i++)
        {
            if (nums[i] <= pivot)
            {
                Swap(nums, i, pivotIndex);
                pivotIndex++;
            }
        }
        Swap(nums, right, pivotIndex);
        return pivotIndex;
    }

    public void Swap(int[] nums, int i, int j)
    {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }

    static void Main(string[] args)
    {
        Solution sol = new Solution();
        int res1 = sol.FindKthSmallest(new int[] { 1, 2, 3, 4, 5, 6 }, 5); // res1 = 5
        int res2 = sol.FindKthSmallest(new int[] { 1, 2, 3, 4, 4, 5, 6 }, 5); // res2 = 4
    }
}
```

## FindKthLargest ([Leetcode 215](https://leetcode.com/problems/kth-largest-element-in-an-array/))
```C#
public class Solution
{
    public int FindKthLargest(int[] nums, int k)
    {
        int resIdx = nums.Length - k;
        int left = 0, right = nums.Length - 1;

        while (left < right)
        {
            int pivLoc = Partition(nums, left, right);

            if (resIdx == pivLoc)
                break;
            else if (resIdx < pivLoc)
                right = pivLoc - 1;
            else
                left = pivLoc + 1;
        }

        return nums[resIdx];
    }

    private int Partition(int[] nums, int left, int right)
    {
        int pivot = nums[right];
        int pivLoc = left;

        for (int i = left; i < right; i++)
        {
            if (nums[i] <= pivot)
            {
                Swap(nums, i, pivLoc);
                pivLoc++;
            }
        }

        Swap(nums, pivLoc, right);

        return pivLoc;
    }

    private void Swap(int[] nums, int i, int j)
    {
        int tmp = nums[i];
        nums[i] = nums[j];
        nums[j] = tmp;
    }
}
```

### References
1. https://en.wikipedia.org/wiki/Quickselect#:~:text=However%2C%20instead%20of%20recursing%20into,of%20O(n2).
