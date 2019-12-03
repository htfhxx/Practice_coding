##### 题目描述
Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.

Example 1:
```
Input: [3,2,1,5,6,4] and k = 2
Output: 5
```
Example 2:
```
Input: [3,2,3,1,2,4,5,5,6] and k = 4
Output: 4
Note:
You may assume k is always valid, 1 ≤ k ≤ array's length.
```

##### 提交链接
https://leetcode.com/problems/kth-largest-element-in-an-array/



##### 代码思路




##### 代码实现
最简单的思路
```
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        if(nums.empty()==true || k<1)
            return false;
        sort(nums.begin(),nums.end());
        return nums[nums.size()-k];
    }
};
```
```
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        if(nums.empty()==true || k<1)
            return false;
        int left=0,right=nums.size()-1;
        while(left<right){
            int tem=partition(nums,left,right);
            if(tem<k-1)
                left=tem+1;
            else if(tem>k-1)
                right=tem-1;
            else
                break;
        }
        return nums[k-1];
    }
    int partition(vector<int>& nums,int left,int right){
        int piv=nums[right];
        int big=left;
        for(int i=left;i<right;i++){
            if(nums[i]>piv){
                swap(nums[big],nums[i]);
                big++;
            }
        }
        swap(nums[right],nums[big]);
        return big;
    }
};



```