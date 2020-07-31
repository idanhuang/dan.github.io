# Kadane's algorithm

In computer science, maximum subarray problem is the task to find a contiguous subarray with the largest sum. This problem was proposed by Uif Grenander in 1977. In 1984, Jay Kadane designed an O(n) algorithm to solve the problem. We call the algorithm "Kadane's algorithm".

## Brute-force approach
We can use brute-force to calculate sum of all possible subarray, and get the maximum subarry sum. Time complexity of brute-force solution will be O(n^3).
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

The brute-force solution can be improved to O(n^2) complexity by using a variable to store the running sum at all possible positions.
```C#
public class Solution {
    public int MaxSubArray(int[] nums) {
        
        if(nums == null || nums.Length == 0)
            return 0;
        
        int maxSum = nums[0];
        
        for(int i = 0; i < nums.Length; i++)
        {
            int currSum = 0;
                
            for(int j = i; j < nums.Length; j++)
            {
                currSum += nums[j];
                maxSum = Math.Max(maxSum, currSum);
            }
        }
        
        return maxSum;
    }
}
```

## Dynamic Programming approach
Instead of picking each index as the starting point of the subarray in the brute-force approach, DP approach picks each index as the ending point. So when calculating sum of the next subarray, the algorithm can take advantage of the previous calculations. sum[i] = sum[i-1] + nums[i] 

This DP approach will improve the time complexity to O(n). It takes O(n) space.

```
public class Solution {
    public int MaxSubArray(int[] nums) {
        
        if(nums == null || nums.Length == 0)
            return 0;
        
        int[] dp = new int[nums.Length];
        dp[0] = nums[0];
        
        for(int i = 1; i < nums.Length; i++)
        {
            dp[i] = Math.Max(dp[i - 1] + nums[i], nums[i]);
        }
        
        return dp.Max();        
    }
}
```




### References
1. https://en.wikipedia.org/wiki/Maximum_subarray_problem
2. https://zhuanlan.zhihu.com/p/85188269
3. https://stackoverflow.com/questions/41904746/why-is-the-maximum-sum-subarray-brute-force-on2
