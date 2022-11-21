---
title: 第5周上机：循环程序设计
layout: post
---

### 第1关：公式计算
```cpp
#include <iostream>
#include <iomanip>

using namespace std;

int main()
{
    int n;
    double s = 1;
    long long n_fac = 1;

    cin >> n;

    for(int i=1; i<=n; i++) {
        n_fac *= i;
        s += 1.0 / n_fac;
    }

    cout << fixed << setprecision(6) << "s = " << s << endl;

    return 0;
}
```

### 第2关：数组排序
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n;
    int a[100];
    cin >> n;

    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (a[j] < a[j + 1]) {
                int t = a[j];
                a[j] = a[j + 1];
                a[j + 1] = t;
            }
        }
    }

    for (int i = 0; i < n; i++) {
        if (i != 0) {
            cout << ' ';
        }
        cout << a[i];
    }
    cout << endl;

    return 0;
}

```

### 第3关：求最大公约数和最小公倍数

```cpp
#include <iostream>
using namespace std;

int main(void)
{
    int m, n, t, a, b;

    cin >> m >> n;

    a = m * n;
    t = m % n;
    while (t != 0) {
        m = n;
        n = t;
        t = m % n;
    }

    cout << "最大公约数是:" << n << endl;
    cout << "最小公倍数是:" << a / n << endl;

    return 0;
}
```

### 第4关：黑洞陷阱

```cpp
#include <iostream>
using namespace std;

#define N (3)

int main()
{
    int n, counter = 0;
    int a[N];

    cin >> n;

    while (n != 495) {
        int max_num = 0, min_num = 0;

        for (int i = 0; i < N; i++) {
            a[i] = n % 10;
            n /= 10;
        }
    
        /* 排序 */
        for (int i = 0; i < N - 1; i++) {
            for (int j = 0; j < N - i -1; j++) {
                if (a[j] < a[j+1]) {
                    int t = a[j];
                    a[j] = a[j+1];
                    a[j+1] = t;
                }
            }
        }

        /* 计算出最大数和最小数 */
        for (int i = 0; i < N; i++) {
            max_num = max_num * 10 + a[i];
        }
        for (int i = N - 1; i >= 0; i--) {
            min_num = min_num * 10 + a[i];
        }
        n = max_num - min_num;

        cout << ++counter << ':' << max_num << '-' << min_num << '=' << n << endl;
    }

    return 0;
}
```

### 第5关：是素数吗

```cpp
#include <iostream>

using namespace std;


int main()
{
    int n, flag = 1;

    cin >> n;

    for (int i=2; i * i <= n; i++) {
        if (n % i == 0) {
            flag = 0;
            break;
        }
    }

    if (flag) {
        cout << "Yes" << endl;
    } else {
        cout << "No" << endl;
    }

    return 0;
}
```

### 第6关：素数和

```cpp
#include <iostream>
using namespace std;

int main()
{
    int n, k;
    int t, m = 0, sum = 0;

    cin >> n >> k;

    for (t = n; t >= 2; t--) {
        int flag = 1;
        for (int i = 2; i * i <= t; i++){
            if (t % i == 0) {
                flag = 0;
                break;
            }
        }
        if (flag) {
            cout << t << " ";
            m++;
            sum += t;
            if (m == k) break;
        }
    }

    cout << sum;

    return 0;
}

```

### 第7关：开灯问题

```cpp
#include <iostream>
using namespace std;

/* 全局数组会自动初始化为0 */
int a[2000];

int main()
{
    int n, k, i, j;
    cin >> n >> k;
    for (i = 1; i <= k; i++) {
        for (j = i; j <= n; j += i) {
            a[j] = !a[j];
        }
    }
    for (i = 1; i <= n; i++) {
        if (!a[i]) continue;
        if (i != 1) {
            cout << ' ';
        }
        cout << i;
    }
    cout << endl;
    return 0;
}

```