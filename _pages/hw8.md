---
title: 第8周作业：函数
layout: post
---

### 第1关：摘苹果
> #### 注意
> 本题的下标是从1开始的，不是从0开始的。
{: .block-tip }

```cpp
int GetApple(int a[], int height, int n)
{
    int count = 0;
    for (int i=1; i<=n; i++) {
        if (a[i] <= height + 30) {
            count++;
        }
    }

    return count;
}

```

### 第2关：魔术师猜数
```cpp
int Magic(int m){
    for(int a = 0; a < 10; a++) {
        for(int b = 0; b < 10; b++) {
            for(int c = 0; c < 10; c++) {
                if (122 * a + 212 * b + 221 * c == m) {
                    return 100 * a + 10 * b + c;
                }
            }
        }
    }
    return -1;
}
```

### 第3关：Fibonacci函数
```cpp
int fib(int i)
{
    if (i == 0) return 1;
    if (i == 1) return 1;

    return fib(i - 1) + fib(i - 2);
}

```

### 第4关：潜泳问题（附加题，选做）
```cpp
#include <iostream>
using namespace std;

int a[2000];

void sort(int a[], int n)
{
    for (int i=0; i<n-1; i++) {
        for (int j=i+1; j<n; j++) {
            if (a[i] > a[j]) {
                int tmp = a[i];
                a[i] = a[j];
                a[j] = tmp;
            }
        }
    }
}

int main()
{
   	int n;
    cin >> n;
    for (int i=0; i<n; i++) {
        cin >> a[i];
    }
    sort(a, n);
    int end = n, cost = 0;
    while(end > 3) {
        int t1 = 2 * a[1] + a[0] + a[end - 1];
        int t2 = 2 * a[0] + a[end - 1] + a[end - 2];
        cost += t1 < t2 ? t1 : t2;
        end -= 2;
    }
    if (end == 3) {
        cost += a[0] + a[1] + a[2];
    } else {
        cost += a[1];
    }
    cout << cost << endl;

    return 0;
}

```