---
title: 第9周上机：指针
layout: post
---

## 1.去掉字符串首尾空格
```
#include <iostream>
using namespace std;

char * trim(char * str);

int main()
{
    char s[1024];     // 定义存储字符串的一维字符数组
    // 输入一行字符，可以包含空格
    // 输入的字符串存入s中，最多读取个字符，后面自动加上'\0'
    cin.getline(s,1024);
    cout << trim(s) << endl;     // 输出去掉首尾空格后的字符串
    return 0;
}

// 函数trim：去掉字符串首尾空格
// 参数：str-字符指针，指向输入的字符串
// 返回值：字符指针，指向去掉首尾空格后的字符串（首地址）
// 提示：可以直接在字符串str中操作
char * trim(char * str)
{
    // 请在此添加代码，实现函数trim
    /********** Begin *********/
    char *p = str;
    while(*p != '\0')
        p++;
    p--;
    while(p >= str && *p == ' ')
    {
        *p = '\0';
        p--;
    }
    p = str;
    while(*p == ' ')
        p++;
    return p;
      
    /********** End **********/
}
```

## 2.用指针实现pswap函数
```
#include <iostream>
using namespace std;

void pswap(int * p, int *q);

int main()
{
    int a, b;
    cin >> a >> b;     // 输入两个整数
    pswap(&a,&b);     // 调用pswap函数，交换a、b的值
    cout << a << " " << b << endl;     // 输出a、b的值
    return 0;
}

//函数pswap：交换指针p和q指向的单元中的整数值
//参数：p,q-int类型指针，指向要交换的整数
void pswap(int * p, int *q)
{
    // 请在此添加代码，实现函数pswap
    /********** Begin *********/
    int a = *p; //p指针指向的值
    *p = *q; //
    *q = a;
    
    
    /********** End **********/
}
```

## 3.选出串中的数字
```
#include <iostream>
using namespace std;

void extractNum(char * str);

int main()
{
    char s[1024];
    cin.getline(s,1024);     // 输入一行字符
    extractNum(s);     // 调用extractNum函数，选出数字
    cout<<s<<endl;     // 输出选出的数字
    return 0;
}

// 函数extractNum：选出str指向的字符串中的数字，并写回str
// 参数：str-指向字符串
void extractNum(char * str)
{
    // 请在此添加代码，实现函数extractNum
    /********** Begin *********/
    char *p=str,*q=str;
    int flag=1;
    while(*q!='\0')
    {
        if(*q=='-' && flag)
        {
            *p++=*q++;
            flag=0;
        }
        else if(*q>='0' && *q<='9')
        {
            flag=0;
            *p++=*q++;
        }
        else
            q++;
    }
    *p='\0';
    
    
    /********** End **********/
}
```

## 4.大写字母好看
```
#include <iostream>
using namespace std;

void toUp(char * str);

int main()
{
    char s[1024];
    cin.getline(s,1024);     // 输入一行字符
    toUp(s);     // 调用toUp函数，转换成大写字母
    cout<<s<<endl;     // 输出变更后的新字符串
    return 0;
}

// 函数toUp：将str指向的字符串中的小写字母变成对应的大写字母
// 参数：str-指向字符串
void toUp(char * str)
{
    // 请在此添加代码，实现函数toUp
    /********** Begin *********/
    char *p=str;
    while(*p != '\0')
    {
        if(*p>='a' && *p<='z')
            *p=*p+'A'-'a';
        p++;
    }
    
    
    /********** End **********/
}
```
