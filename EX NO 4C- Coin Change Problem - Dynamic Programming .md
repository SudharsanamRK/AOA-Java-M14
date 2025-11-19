# EX 4C Coin Change Problem - Dynamic Programming.
## DATE: 20/10/2025

## Aim:
To write a Java program to for given constraints.
You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.

Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

You may assume that you have an infinite number of each kind of coin.

## Algorithm

1. Read the coin denominations and target amount as input.
2. Initialize a `dp` array of size `amount + 1` with a large value (`amount + 1`), and set `dp[0] = 0`.
3. For each amount `i` from `1` to `amount`, iterate through all coin values.
4. If `i - coin >= 0`, update `dp[i] = min(dp[i], dp[i - coin] + 1)` to track the minimum coins needed.
5. After filling the `dp` array, print `dp[amount]` if it’s valid; otherwise, print `-1` if the amount cannot be formed.

## Program:
```txt
Program to implement Coin Change Problem
Developed by: Sudharsanam R K
Register Number:  212222040163
```
```java
import java.util.*;

public class Solution {
    public int coinChange(int[] coins, int amount) {
        int max = amount + 1;
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, max);
        dp[0] = 0; 
        for (int i = 1; i <= amount; i++) {
            for (int coin : coins) {
                if (i - coin >= 0) {
                    dp[i] = Math.min(dp[i], dp[i - coin] + 1);
                }
            }
        }
        return dp[amount] > amount ? -1 : dp[amount];
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution solution = new Solution();
        String coinsLine = scanner.nextLine(); 
        String amountLine = scanner.nextLine();
        coinsLine = coinsLine.replaceAll("[^0-9,]", ""); 
        String[] coinsStr = coinsLine.split(",");
        int[] coins = new int[coinsStr.length];
        for (int i = 0; i < coinsStr.length; i++) {
            coins[i] = Integer.parseInt(coinsStr[i]);
        }
        int amount = Integer.parseInt(amountLine.replaceAll("[^0-9]", ""));
        int result = solution.coinChange(coins, amount);
        System.out.println(result);
        scanner.close();
    }
}
```

## Output:
<img width="273" height="215" alt="image" src="https://github.com/user-attachments/assets/0928ba6a-7bae-40a9-90ce-ffa4e713f1e8" />

## Result:
The program successfully implemented and the expected output is verified.
