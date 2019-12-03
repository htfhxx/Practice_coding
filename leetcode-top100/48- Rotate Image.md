##### 题目描述
You are given an n x n 2D matrix representing an image.

Rotate the image by 90 degrees (clockwise).

Note:

You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.

Example 1:

Given input matrix = 
[
  [1,2,3],
  [4,5,6],
  [7,8,9]
],

rotate the input matrix in-place such that it becomes:
[
  [7,4,1],
  [8,5,2],
  [9,6,3]
]
Example 2:

Given input matrix =
[
  [ 5, 1, 9,11],
  [ 2, 4, 8,10],
  [13, 3, 6, 7],
  [15,14,12,16]
], 

rotate the input matrix in-place such that it becomes:
[
  [15,13, 2, 5],
  [14, 3, 4, 1],
  [12, 6, 8, 9],
  [16, 7,10,11]
]


##### 提交链接

https://leetcode.com/problems/rotate-image/


##### 代码思路
方法一：不太容易想到  
直接操作旋转 90∘90∘ 比较困难，我们可以将它分解成两个操作：  
1. 先以左上-右下对角条线为轴做翻转；  
2. 再以中心的竖线为轴做翻转；  
时间复杂度：O(n2)O(n2)， 额外空间：O(1)  


方法二：  
一次旋转四个数字，一步到位  
关于迭代，可以把每一次迭代看作是一个圈，圈内的每四个元素互换  
迭代次数就是圈的数量  
每圈要交换的数字就是(上边)边长-1  

##### 代码实现
方法一
```
/*
    [1,2,3]
    [4,5,6]
    [7,8,9]

    [7,4,1]
    [8,5,2]
    [9,6,3]
*/
class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        if(matrix.empty()==true)
            return;
        int n=matrix.size();
        for(int i=0;i<n;i++){
            for(int j=i+1;j<n;j++){
                swap(matrix[i][j],matrix[j][i]);
            }
        }
        for(int i=0;i<n;i++){
            for(int j=0;j<n/2;j++){
                swap(matrix[i][j],matrix[i][n-j-1]);
            }
        }
        return;
    }
};


```
方法二
```
/*
    [1,2,3,4]
    [4,5,6,7]
    [7,8,9,10]
    [10,11,12,13]
    
    [1,2,3,4,5]
    [4,5,6,7,8]
    [7,8,9,10,11]
    [10,11,12,13,14] 
    [15,16,17,18,19] 
*/
class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        if(matrix.empty()==true)
            return;
        int n=matrix.size();
        //四个位置互换
        for(int i=0;i<n/2;i++){     //本质上是每次迭代去掉一圈
            for(int j=i;j<n-i-1;j++){  //下一次的圈的上边范围
                swap(matrix[i][j],matrix[j][n-1-i]);  //上 右
                swap(matrix[i][j],matrix[n-1-i][n-1-j]);  //右 下
                swap(matrix[i][j],matrix[n-1-j][i]);  //下 左
            }
        }
        return;
    }
};```