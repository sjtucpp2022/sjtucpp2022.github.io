---
title: 第9周作业：指针
layout: post
---

### 第1关：字符串对调

```cpp
#include <iostream>
using namespace std;

int main()
{
    char str1[20];
    char str2[20];

    cin.getline(str1,20);
    cin.getline(str2,20);

    char *p1 = str1, *p2 = str2;
    while (*p1 && *p2) {
        char tmp = *p1;
        *p1 = *p2;
        *p2 = tmp;
        p1++;
        p2++;
    }
    cout << str1 << endl;
    cout << str2 << endl;

    return 0;
}

```

### 第2关：约瑟夫环问题

```cpp
#include <iostream>
using namespace std;

int flag[10005];

int main()
{
    int n, out = 0, k = 0, j = 0;
    cin >> n;
    for(int i = 1; i <= n; i++) {
        flag[i] = 1;
    }
    while(out < n - 1){
        j = j % n + 1;
        if(flag[j] != 0) k++;
        if(k == 3) {
            flag[j] = 0;
            k = 0;
            out++;
        }
    }

    for(int i = 1; i <= n; i++){
        if(flag[i] != 0) {
            cout << i << endl;
            break;
        }
    }
    return 0;
}

```


### 第3关：加密字符

```cpp
#include <iostream>
using namespace std;

int main()
{   
    char str[40];
    int a[7]={8, 7, 3, 4, 9, 6, 2};

    cin.getline(str, 40);
    for(int i = 0; str[i] != 0; i++) {
        str[i] = str[i] + a[i % 7];
        if(str[i] > 122) str[i] -= 91;
    }
    cout<< str <<endl;
    for(int i = 0; str[i] != 0; i++) {
        str[i] = str[i] - a[i % 7];
        if(str[i] < 32) str[i] += 91;
    }
    cout<< str <<endl;
    return 0;
}
```