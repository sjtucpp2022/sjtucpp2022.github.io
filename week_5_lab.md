### 第五周上机：循环程序设计

#### 1 公式计算
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

#### 2 数组排序
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

#### 3 求最大公约数和最小公倍数

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