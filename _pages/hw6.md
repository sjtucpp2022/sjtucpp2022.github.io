---
title: 第六周作业：数组
layout: post
---

### 第1关：黑色星期五
```cpp
#include <iostream>

using namespace std;

int main()
{
    int y = 1900, m = 1, d = 1;
    int yy, mm = 12, dd = 31;
    cin >> yy;
    yy = 1900 + yy - 1;

    int w[7] = {0, 0, 0, 0, 0, 0, 0};
    int M[13] = {0, 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
    for (int i = 0;; i = (i + 1) % 7)
    {
        if (d == 13)
            w[i]++;
        if (y == yy && m == mm && d == dd)
            break;
        d++;
        if (d > M[m] + (m == 2 && ((y % 4 == 0 && y % 100 != 0) || (y % 400 == 0))))
            m++, d = 1;
        if (m > 12)
            y++, m = 1;
    }
    for (int i = 0; i < 7; i++)
        cout << w[i] << " ";

    return 0;
}

```

### 第2关：删除重复数据（双数组版）

#### 方法1

> 讲第一个数组种的元素不重复得复制到第二个数组中

```cpp
#include <iostream>

using namespace std;

int main()
{
    int a[100], b[100] = {0}, n = 0, m = 0;

    while (cin >> a[n]) {
        n++;
    }

    for (int i=0; i<n; i++) {
        bool appear = false;
        for (int j=0; j<m; j++) {
            if (a[i] == b[j]) {
                appear = true;
                break;
            }
        }
        if (appear == false) {
            b[m++] = a[i];
        }
    }

    for (int i=0; i<m; i++) {
        if (i == 0) {
            cout << b[i];
        } else {
            cout << ' ' << b[i];
        }
    }
    cout << endl;
}
```

#### 方法2

> 用第二个数组来记录第一个数组种数字出现的情况

```cpp
#include <iostream>

using namespace std;

int main(void)
{
    int vis[1010] = {0}, arr[1010], n = 0;
    for (int x; cin >> x;)
        if (vis[x]++ == 0)
            arr[n++] = x;
    for (int k = 0; k < n; k++)
        cout << arr[k] << " ";

    return 0;
}
```

### 第3关：删除重复数据（单数组版）
```cpp
#include <iostream>
using namespace std;

int a[1005];
int main()
{
    int n = 0, i = 0;
    while (cin >> a[n]) {
        n++;
    }
    while (i < n) {
        bool flag = false;

        /* 检查重复元素 */
        for (int j = 0; j < i; j++) {
            if (a[i] == a[j]) {
                flag = true;
                break;
            }
        }

        /* 如果有重复的，则讲后面的数字依次向前移动，否则判断下个数字是否重复 */
        if (flag) {
            for (int j = i; j < n - 1; j++) {
                a[j] = a[j + 1];
            }
            n--;
        } else {
            i++;
        }
    }
    for (int k = 0; k < n; k++) {
        cout << a[k] << ' ';
    }
    cout << endl;
    return 0;
}

```

### 第4关：回文数
```cpp
#include <iostream>
using namespace std;

int main()
{
    int a[10], b[20], B;
    char digit[20];
    cin >> B;

    for (int i=0; i<20; i++) {
        if (i < 10) {
            digit[i] = i + '0';
        } else {
            digit[i] = i - 10 + 'A';
        }
    }

    for(int i=1; i<=200; i++) {
        int n = i * i, len_b = 0;
        bool flag = true;
        while (n > 0) {
            b[len_b] = n % B;
            n /= B;
            len_b++;
        }
        for (int j=0; j<(len_b+1)/2; j++) {
            if (b[j] != b[len_b-j-1]) {
                flag = false;
                break;
            }
        }
        if (flag) {
            int n = i, len_a = 0;
            while (n > 0) {
                a[len_a] = n % B;
                n /= B;
                len_a++;
            }
            for (int j=len_a-1; j>=0; j--) {
                cout << digit[a[j]];
            }
            cout << ' ';
            for (int j=len_b-1; j>=0; j--) {
                cout << digit[b[j]];
            }
            cout << endl;
        }
    }
    return 0;
}

```