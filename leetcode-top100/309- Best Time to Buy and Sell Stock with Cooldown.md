##### 题目描述
Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times) with the following restrictions:

You may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).
After you sell your stock, you cannot buy stock on next day. (ie, cooldown 1 day)
Example:
```
Input: [1,2,3,0,2]
Output: 3 
Explanation: transactions = [buy, sell, cooldown, buy, sell]
```

##### 提交链接
https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/



##### 代码思路

首先的想法是 每一天有两个方面的状态：买or不买、卖or不卖。  
但是这种状态的定义状态的变化，买->卖   买->不卖    不买-> ？  卖->买(不行)  卖->不买   不卖->?  

所以重新定义状态，缩减状态的数量：  

```
当天结束后是否有股票在手：在手has，不在手no  
has[i]=max(no[i-1]-prices[i],has[i-1]);     当天持有，前一天可能持有(当天没卖)，前一天可能没有持有(当天买了)  
no[i]=max(no[i-1],has[i-1]+prices[i]);      当天未持有，前一天可能持有(当天卖了)，前一天可能没有持有(当天和前一天都没买)  
```

还有一个限制：卖了的第二天不能买。  
```
原先的has[i]=max(no[i-1]-prices[i],has[i-1]),   本质上来源于四个状态 
有->无->有   其中这条不能出现  
无->无->有  
有->有->有  
无->有->有  
```
即:
```
no[i-1]=max(no[i-2],has[i-2]+prices[i-1])
变为了
no[i-1]=no[i-2];  

所以：has[i]=max(no[i-2]-prices[i],has[i-1])  
```




##### 代码实现

```
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        if(prices.empty()==true)
            return 0;
        int n=prices.size();
        vector<int> has(n,0);
        vector<int> no(n,0);
        for(int i=0;i<n;i++)
            has[i]=-prices[i];
        for(int i=1;i<n;i++){
            no[i]=max(no[i-1],has[i-1]+prices[i]);
            int tmp=i-1;
            if(i>=2)
                tmp=i-2;
            has[i]=max(no[tmp]-prices[i],has[i-1]);
        }
        return max(has[n-1],no[n-1]); 
    }
};


```
