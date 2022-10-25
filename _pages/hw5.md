---
title: 第五周作业：循环程序设计
layout: post
---

### 第1关：今天星期几
```cpp
#include <iostream>
using namespace std;
int main()
{
    int year, month, day, num;
    cin >> year >> month >> day;
    /* 计算因为年份多出来的天数 */
    for (int i = 2000; i <= year - 1; i++) {
        day += 365;
        if ((i % 4 == 0 && i % 100 != 0) || i % 400 == 0) {
            day += 1;           // 闰年多加1天
        }
    }
    /* 计算因为月份多出来的天数 */
    for (int i = 1; i <= month - 1; i++) {
        if (i == 2) {
            day += 28;          // 平年2月有28天
            if ((year % 4 == 0 && year % 100 != 0) || year % 400 == 0) {
                day += 1;       // 闰年2月多加一天
            }
        } else if (i == 4 || i == 6 || i == 9 || i == 11) {
            day += 30;          // 4 6 9 11月份
        } else {
            day += 31;          // 其他月份 即1 3 5 7 8 10 12
        }
    }
    num = (day + 4) % 7 + 1; 
    cout << "星期" << num << endl;
    return 0;
}
```

### 第2关：求a+aa+aaa+....+aa…aa（n个a）之和
```cpp
#include<iostream>

using namespace std;

int main()
{
    int n, a, sum, a_n = 0;

    cin >> a >> n;

    for (int i=1; i<=n; i++) { 
        a_n = a_n * 10 + a;
        sum += a_n;
    }

    cout << sum << endl;

    return 0;
}

```

### 第3关：求斐波那契数列的第n项

```cpp
#include<iostream>

using namespace std;

int main()
{
    int n;
    long long f_n = 1, a = 0, b = 1;

    cin >> n;

    for (int i=2; i<=n; i++) {
        f_n = a + b;
        a = b;
        b = f_n;
    }

    cout << f_n << endl;

    return 0;
}

```

### 第4关：求f10(n)的值

```cpp
#include <iostream>
using namespace std;

int main(void) {
    int n, f_n;

    cin >> n;
    for(int i=0; i < 10; i++) {
        f_n = 0;
        while (n != 0) {
            f_n += n % 10;
            n /= 10;
        }
        n = f_n;
    }
    cout << f_n << endl;
    
	return 0;
}

```

### 第5关：实现欧几里得算法计算最大公约数

```cpp
#include<iostream>

using namespace std;

int main()
{
    int a, b, r;

    cin >> a >> b;

    while (b > 0) {
        r = a % b;
        a = b;
        b = r;
    }

    cout << a << endl;    

    return 0;
}

```

### 第6关：求x+rev(x)=n的正整数解的个数

```cpp
#include<iostream>

using namespace std;

int main()
{
    int n, counter = 0;

    cin >> n;

    for (int i=1; i<n; i++) {
        int rev = 0, x = i;
        while(x > 0) {
            rev = rev * 10 + x % 10;
            x /= 10;
        }
        if (rev + i == n) {
            counter++;
            // cout << i << endl;
        }
    }

    cout << counter << endl;

    return 0;
}

```

### 第7关：改错题

```cpp
#include<iostream>
#include<iomanip>
using namespace
std;
const double EPS = 1E-6;
int main() {
    int i, n, item;     /* item 可以是long long类型 */
    double e;
    e = 1;
    n = 1;
    
    // item = 1; 
    do {
        item = 1; /* 放到循环里面 */
        for (i = 1; i <= n; i++)
            item *= i;
            // e += 1 / item;   
        e += 1.0 / item;    /* 应该是小数除法 */    
        n++;
    } while (1.0 / item >= EPS);
    // cout <<”e =”<< fixed << setprecision(6) << e << endl;
    cout <<"e ="<<fixed << setprecision(6) << e << endl;        /* 应该使用英文分号 */
    return 0;
}

```

### 第8关：求能带走的物品最大总价值

```cpp

#include<iostream>

using namespace std;

int main()
{
    int n, W, max_val = 0;

    cin >> n >> W;

    for(int i=0; i<W; i++) {
        max_val += n;
        n--;
    }

    cout << max_val << endl;

    return 0;
}

```