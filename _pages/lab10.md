---
title: 第10周上机：指针
layout: post
---

## 1.日期读取
```
#include <iostream>
using namespace std;

void getDate(int& day, int& month, int& year)
{
	// write your code here
    int *p1=&day,*p2=&month,*p3=&year;
    char a[15];
    cin.getline(a,15);
    *p1=10*(a[0]-'0')+(a[1]-'0');
    *p2=10*(a[3]-'0')+(a[4]-'0');
    *p3=1000*(a[6]-'0')+100*(a[7]-'0')+10*(a[8]-'0')+(a[9]-'0');
    
}
// dont change main function
int main()
{
    int day, month, year;
    getDate(day,month,year);
    cout<<" "<<day<<" "<<month<<" "<<year<<endl;
    return 0;
}
```

## 2.删除相同字符
```
#include <iostream>
#include<cstring>
using namespace std;

void deletechar(char* str1, const char* str2) { //str2的值不能改变
	// write your code here
    char *p,*t;
    const char *q=str2;
    int flag=0;
    p=str1; //p指向str1的首地址
    while(*q!='\0'){
        while(*p!='\0'){ //内层循环遍历p，对q的一个字符要和p中每一个字符比较，相同删除
            flag=0;
            if(*p==*q){
                flag=1;
                t=p;
                while(*t!='\0'){ //p位置的字符=q位置的字符，将p所有的字符向前挪一位
                    *t=*(t+1);
                    t++;
                }
            }
            if(!flag) p++; //如果不存在相同的字符，指针向后挪一位，存在相同的字符指针位置不变
            
        }
        p=str1;q++;
    }
    
}

int main() {
	char str1[85], str2[85];
	cin.getline(str1, 80);
    cin.getline(str2, 80);
    
	deletechar(str1, str2);

    cout<<str1<<endl;
	return 0;
}
```

## 3.人工智能
```
#include <iostream>
#include <cstring>
using namespace std;

char * reply(const char * sentence)
{
	// write your code here
    int k;
    k=strlen(sentence);
    if(sentence[k-1]=='!')
        return "Really?!";
    else if(sentence[k-1]=='?')
        return "Emmmm...";
            else
                return "Cool.";
    
}
// dont change main function
int main(void) {
	char str[1005];
    cin.getline(str, 1000);
    char * res = reply(str);
    if (res) cout << res << endl;
    delete [] res;
    return 0;
}
```

## 4.字符串排序
```
#include <iostream>
#include <cstring>
using namespace std;

void swap(string & s1, string & s2)
{
    string temp=s1;
    s1=s2;
    s2=temp;
}
bool Ifless(string & s1,string & s2)
{
    int l1=s1.length(),l2=s2.length(),i=0,j=0,k=0;
    while (s1[k]==s2[k]){
        k++;
    }
    if (k==l1 && l1<l2){
        return true;
    }else if (k==l2 && l2>l1){
        return false;
    }else if (s1[k]<s2[k]) {
        return true;
    } else return false;

}
int main()
{
    int n,i,j;
    string str[100];
    char tmp[100];
    cin >> n;
    cin.get();
    for (i=0;i<n;i++){
        cin.getline(tmp,100);
        str[i]=tmp;
    }
    for (i=0;i<n;i++){
        for (j=i+1;j<n;j++){
            if (Ifless(str[i],str[j]))
            swap(str[i],str[j]);
        }
    }
    for (i=0;i<n;i++) {
        cout << str[i] << endl;
    }
    return 0;
}
```

## 5.数值积分
```
#include <iostream>
#include <cmath>
#include <iomanip>
using namespace std;

double f(double x) {
    return exp(-x*x);
}
double integrate(double (*pf)(double), double a, double b)
{
    // write your code here
    double x,num=0;
    x=(b-a)/1000000;
    for(int i=0;i<1000000;i++){
        num+=f(a+i*x)*x;
    }
    return num;
}


int main(void) {
    double a, b;
    cin >> a >> b;
    cout << fixed << setprecision(5) << integrate(&f, a, b) << endl;
    return 0;
}
```
