# 55.跳跃游戏

给定一个非负整数数组，你最初位于数组的第一个位置。

数组中的每个元素代表你在该位置可以跳跃的最大长度。

判断你是否能够到达最后一个位置。

[原题链接](https://leetcode-cn.com/problems/jump-game/)

## 解法1 动态规划
 - 从前向后遍历，找到每个元素只跳一步的话，可达的最大位置。
 - 如果前一个元素不可达到当前元素，则返回
 Java代码
```
class Solution {
    public boolean canJump(int[] nums) {
        int len=nums.length;
        int dp=nums[0];
        for(int i=1;i<len;i++){
            if(i>dp){
                return false;
            }
            dp=Math.max(dp,nums[i]+i);
        }
        return true;
    }
}
```

## 解法2 步步为营
 - 从后向前遍历数组
 - 判断当前位置能够到达终点，则将当前位置当作新的终点
 - 只有遇到0时，才会发生不可达的事件
Java代码
```
class Solution {
    public boolean canJump(int[] nums) {
        int len=nums.length;
        int n=0;
        for(int i=len-2;i>=0;i--){
            if(nums[i]>n++){
                n=0;
            }
        }
        return n==0;
    }
}
```
