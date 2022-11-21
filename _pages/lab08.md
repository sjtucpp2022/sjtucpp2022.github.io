---
title: 第8周上机：函数
layout: post
---
** Coming soon~ **
## 1.完全数
```
#include<iostream>
using namespace std;

bool perfectNumber(int n)
{
	/** Begin **/
    int i,m=0;
    bool flag;
    for (i=1 ; i < n ; i++){
        if (n%i==0)
        {
         m+=i;
        }
    }
    if (m==n)
    {
        flag=true;
    }
    return flag;
    /**  End  **/
}

int main()
{
    int m, n;
    cin >> m >> n;
    /** Begin **/
    int i;
    bool flag=false;
    for (i=m ; i <= n ; i++){
        if (perfectNumber(i))
        {
            cout << i << " " ;
            flag=true;
        }
    }
    if (!flag)
    {
        cout << "-1" << endl;
    }
    else 
    {
        cout << endl;
    }
    /**  End  **/
    
    return 0;
}
```

## 2.组合数
```
#include<iostream>  
using namespace std; 
 
long long factorial(int n)
{
	if(n==1){return 1;}
    if(n==0){return 1;}
    else {return n*factorial(n-1);} //递归求n！
}

int main()
{
	int n,m;
    cin>>n>>m;
    cout<<factorial(n)/(factorial(m)*factorial(n-m));
    return 0;
}
```
## 3.冰雹猜想
```
#include<iostream>
using namespace std;
void valid(int n)
{
	/** Begin **/
    cout << n << " ";
    while(n!=1)
    {
        if (n%2==0)
        {
            n/=2;
        }
        else 
        {
            n=n*3+1;
        }
        cout << n << " ";
    }
    cout << endl;
    /**  End  **/
}

int main()
{
    int n;
    cin >> n;
    valid(n);
    return 0;
}
```
## 4.统计正整数中指定数字的个数
```
#include<iostream>
using namespace std;

int CountDigit(int number,int digit)
{
	/** Begin **/
    int n=0;
    while(number!=0){
        if(number%10==digit)
            n+=1;
        number/=10;
    }
    return n;
    /**  End  **/
}

int main()
{
	int number, digit;
	cin >> number >> digit;
	cout << CountDigit(number,digit) <<endl;
    
	return 0;
}
```
## 5.递归法计算两个数的最大公约数
```
#include<iostream>
using namespace std;

int Gcd(int a, int b)
{
	// write your code here
    if (a>b) 
    {
        return Gcd(a-b,b);
    }
    else if (b>a)
    {
        return Gcd(a,b-a);
    }
    else
    {
        return a;
    }
}

int main()
{
	// write your code here
    int a,b;
    cin >>a>>b;
    cout << Gcd(a,b) << endl;
	return 0;
}
```

