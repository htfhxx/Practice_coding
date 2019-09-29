##### 题目描述
Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

Note: You may not slant the container and n is at least 2.


##### 提交链接

https://leetcode.com/problems/container-with-most-water/


##### 代码思路

1. 最简单的方式就是两两结合得到n^(2) 个组合，求最大值，复杂度O(n^2)  
2. 面积=宽×高，那么我们从最大的宽度开始，逐步缩小宽度，探索宽度，过程中保存最大值。  
最大的宽度就是0 ~ (n-1)，缩短宽度的过程是将左指针右移或者右指针左移。   
第一次移动，宽度减一的情况下应该使高度尽可能大，因此移动的应该是高度较低的指针。





##### 代码实现

```
class Solution {
public:
    int maxArea(vector<int>& height) {
        if(height.size()<=1)
            return 0;
        int i=0,j=height.size()-1;
        int result=0;
        while(i<j){
            int tmpResult=(j-i)*min(height[i],height[j]);
            result=max(result,tmpResult);
            if(height[i]<height[j])
                i++;
            else
                j--;

        }
        return result;
    }
};


```
