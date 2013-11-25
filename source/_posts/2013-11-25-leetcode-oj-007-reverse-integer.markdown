---
layout: post
title: "LeetCode OJ 007 Reverse Integer"
date: 2013-11-25 20:12:54 +0800
comments: true
categories: LeetCode
---
>[Reverse Integer 整数倒转](http://oj.leetcode.com/problems/reverse-integer/#)

###Description:
>Reverse digits of an integer.  
>Example1: x = 123, return 321  
>Example2: x = -123, return -321  
  
####_Have you thought about this?_  
>Here are some good questions to ask before coding. Bonus points for you if you have already thought through this!  
>If the integer's last digit is 0, what should the output be? ie, cases such as 10, 100.  
>Did you notice that the reversed integer might overflow? Assume the input is a 32-bit integer,  
>then the reverse of 1000000003 overflows. How should you handle such cases?  
>Throw an exception? Good, but what if throwing an exception is not an option?  
>You would then have to re-design the function (ie, add an extra parameter).
<!--more-->
###描述:
>反转一个整数的数字位。  
例1: x = 123, return 321  
例2: x = -123, return -321  
  
####_你有想过吗？_  
>以下是在编写代码之前值得想一下的问题，如果你已经想到了，给你一个Yes!  
>如果整数的后几位是0，那么反转之后是多少？比如10，100。  
>你有注意到吗，一些数字反转后会出现溢出现象。  
>假设输入时32字节的整数，那么反转1000000003就会出现溢出，应该怎么处理呢？  
>抛出一个异常？很好，如果不允许抛出异常呢？  
>那么你需要重新设计这个函数了(添加一个额外的参数)。  

###思路:
>先记录输入数字的正负情况，然后将其转换成正数来处理。  
>每次取输入数字的最后一位加到输出结果的后面一位。  
>如果输入为整数，计算出的输出为负数，则出现溢出。  

###代码:
```cpp Reverse Integer
class Solution {
public:
    int reverse(int x) {
        // IMPORTANT: Please reset any member data you declared, as
        // the same Solution instance will be reused for each test case.
        bool positive = true;
        if(x < 0) {
        	positive = false;
        	x = -x;
        }
        int result = 0;
        while(x) {
        	result = result*10 + x%10;
        	x /= 10;
        }
        if(result<0) {
        	return -1;
        }
        if(!positive) {
        	result *= -1;
        }
        return result;
    }
};
```