---
title: 第14周上机：类
layout: post
---

## 1.教授是老师

- `main.cpp`

```
#include <iostream>
#include <cstring>

#include "birthday.h"
#include "teacher.h"
#include "professor.h"

using namespace std;

int main()
{
    int num,year,month,day;
    char a[80],b[80],*name,*sex,c;
    name=a; sex=b;
    cin>>num;
    cin>>a;
    c=getchar();
    cin.getline(b,80);
    cin>>year>>month>>day;
    professor prof(num,name,sex,year,month,day);
    int newy,newm,newd;
    cin>>newy>>newm>>newd;
    prof.change(newy,newm,newd);
    prof.play();
    return 0;
}
```

- `birthday.h`

```
#ifndef BIRTHDAY_H
#define BIRTHDAY_H
#include <cstring>
#include <iostream>

using namespace std;

class birthday
{
private:
    int year;
    int month;
    int day;
public:
    birthday(int y,int m,int d);
    void dis();
    void set(int a,int b,int c);
};

#endif /* BIRTHDAY_H */
```

- `birthday.cpp`

```
#include "birthday.h"
#include <cstring>
#include <iostream>
using namespace std;

birthday::birthday(int y,int m,int d){
    year=y;
    month=m;
    day=d;
}

void birthday::dis(){
    cout<<"birthday:"<<year<<'/'<<month<<'/'<<day<<endl;
}

void birthday::set(int a,int b,int c){
    year=a;
    month=b;
    day=c;
}
```

- `teacher.h`

```
#ifndef TEACHER_H
#define TEACHER_H
#include <cstring>
#include <iostream>

using namespace std;

class teacher
{
private:
    int num;
    char *name;
    char *sex;
public:
    teacher(int nu,char *na,char *se);
    void display();
};

#endif /* TEACHER_H */
```

- `teacher.cpp`

```
#include "teacher.h"
#include <iostream>
using namespace std;

teacher::teacher(int nu,char *na,char *se){
    num=nu;
    name=na;
    sex=se;
}

void teacher::display(){
    cout<<"num:"<<num<<endl;
    cout<<"name:";
    for(int i=0;name[i];++i) cout<<name[i];
    cout<<endl;
    cout<<"sex:";
    cout<<sex;
    cout<<endl;
}
```

- `professor.h`

```
#ifndef PROFESSOR_H
#define PROFESSOR_H
#include <cstring>
#include "birthday.h"
#include "teacher.h"

using namespace std;

class professor:public teacher
{
public:
    professor(int nu,char *na,char *se,int y,int m,int d);
    birthday birth;
    void play();
    void change(int a,int b,int c);
};

#endif /* PROFESSOR_H */
```

- `professor.cpp`

```

#include "professor.h"
#include <iostream>
using namespace std;

professor::professor(int nu,char *na,char *se,int y,int m,int d)
:teacher(nu,na,se), birth(y,m,d){}

void professor::play(){
    display(); //teacher类的display()
    birth.dis();
}
void professor::change(int a,int b,int c){
    birth.set(a,b,c);
}
```

## 2.建筑类

- `main.cpp`

```
#include <iostream>
#include "house.h"
#include "office.h"
#include "building.h"

using namespace std;

int main()
{
	Building build1(18,360,8000);
	build1.print();
	House house(6,24,2880,4,2);
	house.print();
	Office office(18,360,8000,4,4);
	office.print();    
    return 0;
}
```

- `building.h`

```
#ifndef BUILDING_H
#define BUILDING_H

class Building
{
	int layernumber;
	int housenum;
	float sumarea;
public:
	Building();
	Building(int m,int n,float s);
	void print();
};

#endif /* BUILDING_H */
```

- `building.cpp`

```
#include "building.h"
#include <iostream>
using namespace std;

Building::Building(int m,int n,float s)
{
	cout<<"base constructor called."<<endl;
	layernumber=m;housenum=n;sumarea=s;
}

void Building::print()
{
	cout<<"this is a "<<layernumber<<"-story building"<<endl;
	cout<<"there are "<<housenum<<" houses"<<endl;
	cout<<"And total area is "<<sumarea<<endl;
}
```

- `house.h`

```
#ifndef HOUSE_H
#define HOUSE_H
#include "building.h"
class House: public Building
{
private:
    int bedroomnum;
    int bathroomnum;
public:
	House(int m,int n,float s,int num1,int num2);
	void print();
};



#endif /* HOUSE_H */
```

- `house.cpp`

```
#include "house.h"
#include "building.h"
#include <iostream>
using namespace std;

House::House(int m,int n,float s,int num1,int num2): Building(m,n,s)
{
    cout<<"House constructor called."<<endl;
	bedroomnum=num1;
    bathroomnum=num2;
}

void House::print()
{
    Building::print();
    cout << "bedroomnum=" << bedroomnum << endl;
    cout << "bathroomnum=" << bathroomnum << endl;
}
```

- `office.h`

```
#ifndef OFFICE_H
#define OFFICE_H
#include "building.h"
class Office: public Building
{
private:
    int stuffnum;
    int telnum;
public:
	Office(int m,int n,float s,int num1,int num2);
	void print();
};



#endif
```

- `office.cpp`

```
#include "office.h"
#include "building.h"
#include <iostream>
using namespace std;

Office::Office(int m,int n,float s,int num1,int num2): Building(m,n,s)
{
    cout<<"Office Constructor called."<<endl;
	stuffnum=num1;
    telnum=num2;
}

void Office::print()
{
    Building::print();
    cout << "stuffnum=" << stuffnum << endl;
    cout << "telnum=" << telnum << endl;
}
```
