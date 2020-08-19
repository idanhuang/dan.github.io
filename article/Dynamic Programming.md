# Dynamic Programming

## What is dynamic programming

Dynamic programming was developed by Richard Bellman in the 1950s. It is a technique for solving an optimization problem by breaking it down into simpler subproblems, and utilizing the fact that the optimal solution to the overall problem depends upon the optimal solution to its subproblems.

Why it is called dynamic programming"?

## Properties of dynamic programming questions



## Recursive
```C#
public int Fibonacci(int n)
{
    if (n < 2)
        return n;

    return Fibonacci(n - 1) + Fibonacci(n - 2);
}  
```

## Bottom Up (Tabulation)
```C#
public int Fibonacci(int n)
{
    if (n < 2)
        return n;

    int[] dp = new int[n + 1];
    dp[0] = 0;
    dp[1] = 1;

    for (int i = 2; i < n + 1; i++)
        dp[i] = dp[i - 1] + dp[i - 2];

    return dp[n];
}
```

## Top Down (Memoization)
```C#
public int[] memo;

public void InitializeMemo(int n)
{
    memo = new int[n + 1];
    for (int i = 0; i < memo.Length; i++)
    {
        memo[i] = -1;
    }
}

public int Fibonacci(int n)
{
    if (memo[n] == -1)
    {
        if (n < 2)
            memo[n] = n;
        else
            memo[n] = memo[n - 1] + memo[n - 2];
    }

    return memo[n];
}
```
