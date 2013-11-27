---
layout: post
title: "LeetCode OJ 008 String to Integer(atoi)"
date: 2013-11-27 14:07:03 +0800
comments: true
categories: LeetCode
---
>[String to Integer (atoi) 字符串转换为整数](http://oj.leetcode.com/problems/string-to-integer-atoi/)

###Description:
>Implement atoi to convert a string to an integer.  

* **Hint:**  
>Carefully consider all possible input cases. If you want a challenge, please do not see below and ask yourself what are the possible input cases.  
* **Notes:**  
>It is intended for this problem to be specified vaguely (ie, no given input specs). You are responsible to gather all the input requirements up front.  

<!--more-->

* **Requirements for atoi:**  
>The function first discards as many whitespace characters as necessary until the first non-whitespace character is found. Then, starting from this character, takes an optional initial plus or minus sign followed by as many numerical digits as possible, and interprets them as a numerical value.  
The string can contain additional characters after those that form the integral number, which are ignored and have no effect on the behavior of this function.  
If the first sequence of non-whitespace characters in str is not a valid integral number, or if no such sequence exists because either str is empty or it contains only whitespace characters, no conversion is performed.  
If no valid conversion could be performed, a zero value is returned. If the correct value is out of the range of representable values, INT_MAX (2147483647) or INT_MIN (-2147483648) is returned.  

###描述:
>实现atoi来把字符串string转换为整数integer。

* **提示:**  
>仔细考虑输入的所有可能情况。如果你想要挑战一下，请不要继续向下看，问问自己输入有哪些情况。  
* **注意:**  
>本问题的目的是不给出输入的详细情况。由你来负责考虑输入要求。  
* **atoi的要求:**  
>首先忽略前置空格。  
字符串中数字后面可以包含其他字符，但是这些字符被忽视。  
如果前置空格后紧跟着的不是数字或正负符号，或者字符串为空，或者只包含空格，则不需要进行转换。  
如果数字溢出则返回INT_MAX(2147483647)或者INT_MIN(-2147483648)。  


###思路:
>先滤去前置空格，再记录正负符号，再滤去前导0。
>记录数字，若溢出则根据正负符号返回INT_MAX(2147483647)或者INT_MIN(-2147483648)。  


###代码:
```cpp String to Integer(atoi)
class Solution {
public:
    int atoi(const char *str) {
        // IMPORTANT: Please reset any member data you declared, as
        // the same Solution instance will be reused for each test case.
        bool positive = true;
        const char *p=str;
        for(; *p==' '; p++) {
        }
        if(*p=='-') {
            positive = false;
            p++;
        }
        if(*p=='+') {
            p++;
        }
        for(; *p=='0'; p++) {
        }

        int result = 0;
        for(; p; p++) {
            if(*p<48 || *p>57) {
                break;
            }
            if(result > (INT_MAX-(*p-48))/10) {
                if(positive) {
                    return INT_MAX;
                } else {
                    return INT_MIN;
                }
            }
            result = result*10+(*p-48);
        }
        if(!positive) {
            result *= -1;
        }
        return result;
    }
};
```