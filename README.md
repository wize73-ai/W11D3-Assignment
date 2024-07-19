# W11D3-Assignment
Solving the Coin Change Problem

 

Objective:

Strengthen your understanding of dynamic programming by solving the Coin Change problem on LeetCode and documenting your solution approach.

 

Problem Statement:

Solve the LeetCode problem: https://leetcode.com/problems/coin-change/description/Links to an external site.

 

Steps to Complete the Exercise:

Understand the Problem:
   - Carefully read the problem statement.

You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.

Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

You may assume that you have an infinite number of each kind of coin.

   - Identify the inputs and expected outputs.

Input: coins = [1,2,5], amount = 11
Output: 3
Explanation: 11 = 5 + 5 + 1

Input: coins = [2], amount = 3
Output: -1

Input: coins = [1], amount = 0
Output: 0

   - Note the constraints and possible edge cases.

1 <= coins.length <= 12
1 <= coins[i] <= 231 - 1
0 <= amount <= 104

Note example 2, where only 2c coins cannot add up to three, must return -1

Plan Your Approach:
   - Consider different dynamic programming strategies to solve the problem.

   greedy approach from class:
   
   class Solution(object):
    def coinChange(self, coins, amount):
        coins.sort(reverse=True) # Sort coins lg too sm so try largest to smallest value coin
        num_coins = 0
        for coin in coins:
            if amount == 0:
                break
            count = amount // coin # Use floor division to spend as many of selected coin value
            num_coins += count #update the coin coint
            amount -= count * coin # update the remainder until remainder zero trriggering a break
        return num_coins if amount == 0 else -1

    dynamic programming approach

    class Solution(object):
        def coinChange(self, coins, amount):dp = [float('inf')] * (amount + 1)dp = [float('inf')] * (amount + 1)
        dp[0] = 0
        for coin in coins:
            for x in range(coin, amount + 1):
                dp[x] = min(dp[x], dp[x - coin] + 1)
        return dp[amount] if dp[amount] != float('inf') else -1

   - Choose between memoization and tabulation approaches.

   - Outline your solution before coding.
   
Sort coin list from big to small, so when you iterate you can find the smallest number first ie 63 2 quarters one dime three pennies = 2+1+3 = 6 vs 63 pennies = 63

iterate through the coin values using floor division // to determone how many coins it can take of that denom. update the count of coins, update the remainder, check next smallest denom until the remainder is zero

return the leaast amount of coins to return a zero remainder.

return -1 if there is no logical solution   my first time using float'inf' as placeholder

Write the Code:
   - Use your preferred coding environment.

   Python 3

   - Implement your solution clearly and concisely.

   - Use meaningful variable names and comments to explain your code.

Test Your Solution:
   - Test your code with various test cases, including edge cases.

   - Ensure your solution passes all test cases on LeetCode.

Document Your Solution:
   - Create a documentation file in PDF or Markdown format.

   - Explain your code design choices.

   - Describe the dynamic programming approach used (memoization or tabulation).

   i used tabulation, iterating through the coin values from high to low for the logical minu=imum

   vs 

   Memoization would require recursion and every permutation possible, seems less intuitive but guaranteed to get every possible result.

   tabulation would keep the time and space complexities much lower.

   - Detail your approach and reasoning for solving the problem.

Submit Your Solution:
   - Ensure your solution passes the LeetCode submission.

   please see screenshots in repo

   - Submit your documentation and LeetCode solution via the designated platform.

