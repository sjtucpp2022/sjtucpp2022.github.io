## 1.个人成绩单
```
//class.cpp
#include "class.h"
#include<cstring>
using namespace std;

PersonScore::PersonScore(const char * i, const char * n, int m, int e, int c) {
    // Your code goes here
    strcpy(id,i);
    strcpy(name,n);
}

void PersonScore::GiveValue(int m, int e, int c){
    // Your code goes here
    math=m;
    English=e;
    CS=c;
}

void PersonScore::Display(){
    // Your code goes here
    cout<<id<<' '<<name<<' '<<math<<' '<<English<<' '<<CS<<endl;
}

int PersonScore::GetHigh(){
    // Your code goes here
    int a=math,b=English,c=CS;
    if(a<b){swap(a,b);}
    if(a<c){swap(a,c);}
    return a;
}

int PersonScore::GetLow(){
    // Your code goes here
    int a=math,b=English,c=CS;
    if(a>b){swap(a,b);}
    if(a>c){swap(a,c);}
    return a;
}

bool PersonScore::isMathPass(){
    // Your code goes here
    if(math>=60){ return true;}
    else return false;
}

bool PersonScore::isEnglishPass(){
    // Your code goes here
    if(English>=60){ return true;}
    else return false;
}

bool PersonScore::isCSPass(){
    // Your code goes here
    if(CS>=60){ return true;}
    else return false;
}
```

## 2.wall类
```
//main.cpp
#include<iostream>
#include "class.h"

using namespace std;

int wall::extra_data = 1;
int main(){
    //7 objects are instantiated, including an array
    wall small, medium, large, group[4];

    /******** Your code start here**********/
    int l,w;
    cin >>l>>w;
    small.set(l,w);
    cin >>l>>w;
    medium.set(l,w);
    cin >>l>>w;
    large.set(l,w);
    for (int i=0 ; i < 4 ; i++){
        cin >>l>>w;
        group[i].set(l,w);
    }

    /********** end your code *****************/
    cout<<"Area of the small wall is "<<small.get_area()<<"\n";

    cout<<"Area of the medium wall is "<<medium.get_area()<<"\n";

    cout<<"Area of the large wall is "<<large.get_area()<<"\n";


    for(int index=0; index<4; index++)
    {
        cout<<"An array of wall area "<<index<<" is "<<group[index].get_area()<<"\n";
    }


    cout<<"Extra data value is "<<small.get_extra()<<"\n";
    cout<<"New Extra data value is "<<medium.get_extra()<<"\n";
    cout<<"New Extra data value is "<<large.get_extra()<<"\n";
    cout<<"New Extra data value is "<<group[0].get_extra()<<"\n";
    cout<<"New Extra data value is "<<group[3].get_extra()<<"\n";
    return 0;
}

//class.cpp
#include <iostream>
#include "class.h"

using namespace std;

wall :: wall(){}
void wall :: set(int new_length, int new_width)
{
    length=new_length;
    width=new_width;
}
int wall :: get_area()
{
    int area;
    area=length*width;
    return area;
}
int wall :: get_extra()
{
    return extra_data++;
}
```

## 3.坐标点类
```
#include "class.h"

// Your code goes here
Point::~Point(){}
Point::Point(double nx, double ny){
    x=0.0;
    y=0.0;
}
Point::Point(Point &np){}
void Point::SetX(double nx){
    x=nx;
}
void Point::SetY(double ny){
    y=ny;
}
void Point::SetPoint(double nx, double ny){
    x=nx;
    y=ny;
}
void Point::SetPoint(Point &np){
    x=np.x;
    y=np.y;
}
```

## 4.大整数类
```
//class.h
#ifndef CLASS_H
#define CLASS_H

class big{
    friend void du(big &p);
    char n1[1001],n2[1001];
    int nn1,nn2;
    
public:
    void plus();
    
};



#endif /* CLASS_H */

//class.cpp
#include <iostream>
#include "class.h"
#include <cstring>

using namespace std;


void big::plus(){
    int tp,jin=0;
    int sum[1001]={0},i;

    //计算长度重合部分
    for(i=0;i<nn1&&i<nn2;i++){    
        tp=(n1[nn1-1-i]-'0'+n2[nn2-1-i]-'0');
        tp+=jin;
        jin=0; //上一次运算的进位
        if(tp>=10){
            sum[i]=tp-10;
            jin=1;
        }
        else sum[i]=tp;
    }

    //计算长度不重合部分
    if(nn1==nn2){
        if(jin)sum[i]=1;
        else i--;
    }
    if(nn1>nn2){
        for(;i<nn1;i++){
            tp=(n1[nn1-1-i]-'0');
            tp+=jin;
            jin=0;
            if(tp>=10){
                sum[i]=tp-10;
                jin=1;
            }
            else sum[i]=tp;
        }
        if(jin)sum[i]=1;
        else i--;
    }
    if(nn2>nn1){
        for(;i<nn2;i++){
            tp=(n2[nn2-1-i]-'0');
            tp+=jin;
            jin=0;
            if(tp>=10){
                sum[i]=tp-10;
                jin=1;
            }
            else sum[i]=tp;
        }
        if(jin)sum[i]=1;
        else i--;
    }

    for(;i>=0;i--){
        cout<<sum[i];
    }
}

//main.cpp
#include <iostream>
#include "class.h"
#include <cstring>

using namespace std;

void du(big &p){
    cin.getline(p.n1,1001,'\n');
    p.nn1=strlen(p.n1);
    
    cin.getline(p.n2,1001,'\n');
    p.nn2=strlen(p.n2);
}
int main(){
    big p;
    du(p);
    p.plus();

    return 0;
}

```
