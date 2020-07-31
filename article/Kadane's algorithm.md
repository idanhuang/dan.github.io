# Kadane's algorithm

In computer science, maximum subarray problem is the task to find a contiguous subarray with the largest sum. This problem was proposed by Uif Grenander in 1977. In 1984, Jay Kadane designed an O(n) algorithm to solve the problem. We call the algorithm "Kadane's algorithm".

## Brute-force
We can use brute-force to calculate sum of all the possible subarray, and get the maximum subarry sum. Time complexity of brute-force solution will be O(n^3).
```C#
public class Solution {
    public int MaxSubArray(int[] nums) {
        
        if(nums == null || nums.Length == 0)
            return 0;
        
        int maxSum = nums[0];
        
        for(int i = 0; i < nums.Length; i++)
        {
            for(int j = i; j < nums.Length; j++)
            {
                int currSum = 0;
                
                for(int k = i; k <= j; k++)
                {
                    currSum += nums[k];
                }
                
                maxSum = Math.Max(maxSum, currSum);
            }
        }
        
        return maxSum;
    }
}
```

### References
1. https://en.wikipedia.org/wiki/Maximum_subarray_problem
2. https://zhuanlan.zhihu.com/p/85188269
