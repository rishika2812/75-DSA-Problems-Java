## **Problem Description:**

You are given an array **prices** where **prices[i]** is the price of a given stock on the **ith**  day.

You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.

Return *the maximum profit you can achieve from this transaction*. If you cannot achieve any profit, return **0**.

## Solutions:

### **Approach 1:**

Need to try every pair.

For each i, checking all j>i and computing: profit = prices[j] - prices[i], and get the maximum profit.

```java
class Solution {
    public int maxProfit(int[] prices) {
        int maxProfit = 0;
        
        for(int i = 0; i < prices.length; i++) {
            for(int j = i + 1; j < prices.length; j++) {
                int profit = prices[j] - prices[i];
                maxProfit = Math.max(maxProfit, profit);
            }
        }
        
        return maxProfit;
    }
}

```

TC: O(n^2)

SC: O(1)

### Approach 2:

- Initialize:
    - minPrice = prices[0]
    - maxProfit = 0
- Traverse array:
    - Update minPrice if current price is smaller
    - Else calculate profit and keep updating maxProfit.

```java
class Solution {
    public int maxProfit(int[] prices) {
        int minPrice = prices[0];
        int maxProfit = 0;
        
        for(int i = 1; i < prices.length; i++) {
            if(prices[i] < minPrice) {
                minPrice = prices[i];
            } else {
                int profit = prices[i] - minPrice;
                maxProfit = Math.max(maxProfit, profit);
            }
        }
        
        return maxProfit;
    }
}
```

TC: O(n)

SC: O(1)