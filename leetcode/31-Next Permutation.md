##### 题目描述
Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.

If such arrangement is not possible, it must rearrange it as the lowest possible order (ie, sorted in ascending order).

The replacement must be in-place and use only constant extra memory.

Here are some examples. Inputs are in the left-hand column and its corresponding outputs are in the right-hand column.

1,2,3 → 1,3,2
3,2,1 → 1,2,3
1,1,5 → 1,5,1


##### 提交链接
https://leetcode.com/problems/next-permutation/



##### 代码思路
如果数组是纯逆序[5,4,3,2,1]，则全部翻转
如果数组[5,3,4,2,1]出现顺序对<a,b>=<3,4>:
1. 找到a_index和b_index的位置(并且b-a尽可能小)
2. 交换a和b得到[5,4,3,2,1]
3. 再将a_index后的数字全部翻转得到[5,4,1,2,3]

9 6 5 3 1 
9 3 6 5 1 -> 9 5 6 3 1

ps: for语句比while简洁很多

##### 代码实现
```
class Solution {
public:
    void nextPermutation(vector<int>& nums) {
        if(nums.empty()==true)
            return;
        int n=nums.size();
        int i;
        for(i=n-2;i>=0;i--){
            if(nums[i]<nums[i+1])
                break;
        }
        if(i==-1)
            reverse(nums,0,n-1);
        else{
            int j;
            for(j=n-1;j>i;j--){
                if(nums[j]>nums[i])
                    break;
            }
            swap(nums[i],nums[j]);
            reverse(nums,i+1,n-1);
        }
    }
    void reverse(vector<int> & nums,int left, int right){
        while(left<right)
            swap(nums[left++],nums[right--]);
    }
};
```
