---
title: 第7周作业：字符数组、函数
layout: post
---

### 第1关：改错题

```cpp
// 请在下方修改代码
/********** Begin *********/
#include <iostream>
using namespace std;

int main(){
    int i, j, n = 0;
    char str[80];

    i = 0;
    while((str[i]=cin.get())!='\n')
        i++;
    str[i] = '\0';

    for(j = 0; str[j]!=0; j++){
        // if(str[j]>='0'||str[j]<='9')
        //     n = n*10 + str[j];
        if(str[j]>='0' && str[j]<='9')      // || 改为 &&
            n = n*10 + (str[j] - '0');      // str[j]改为(str[j] - '0');
    }
    cout << n << endl;
    return 0;
}
/********** End *********/
```

### 第2关：查找字符

```cpp
#include <iostream>
#include <cstring>
using namespace std;

int main()
{
    char str[100], ch, i = 0;
    int index = -1;

    cin.getline(str, 100);
    ch = cin.get();

    for (int i = 0; str[i] != '\0'; i++) {
        if (str[i] == ch) {
            index = i;
        }
    }

    if (index >= 0) {
        cout << "Index=" << index << endl;
    } else {
        cout << "Not Found" << endl;
    }

    return 0;
}

```

### 第3关：字符数统计

> #### 注意事项
> 掌握cin.getline的使用方法，可以极大地方便长文本的输入。
{: .block-tip }

```cpp
#include <iostream>
#include <cstring>
using namespace std;

const int maxn = 100;

int main()
{
    int letter_count = 0, digit_count = 0, other_count = 0, n = 0;
    char str[maxn];

    cin >> n;
    cin.get();
    for (int i = 0; i < n; i++) {
        cin.getline(str, maxn);
        for (int j = 0; str[j] != '\0'; j++) {
            if ((str[j] >= 'A' && str[j] <= 'Z') || (str[j] >= 'a' && str[j] <= 'z')) {
                letter_count++;
            } else if (str[j] >= '0' && str[j] <= '9') {
                digit_count++;
            } else if (str[j] != ' ' && str[j] != '\t' && str[j] != '\n') {
                other_count++;
            }
        }
    }

    cout << "英文字母：" << letter_count << endl;
    cout << "数字：" << digit_count << endl;
    cout << "其他字符：" << other_count << endl;

    return 0;
}

```

### 第4关：查找回文字符串（选做）


> #### 解题思路
> - 方法一：本关查找回文字符串的思路为：以一个字符为中心，向两端扩展，需要分长度奇数和偶数两种情况，[时间复杂度](https://zhuanlan.zhihu.com/p/110707881)为$O(n^2)$；
> - 方法二：使用一个双层循环，在循环内部判断字符串从$i$到$j (0<=i<j<n)$的子字符串是否为回文字符串，[时间复杂度](https://zhuanlan.zhihu.com/p/110707881)为$O(n^3)$；
> - 方法三：动态规划。
>
> 这里提供方法一的代码：
{: .block-tip }


```cpp
#include <iostream>
#include <cstring>

using namespace std;

const int maxn = 510;
char raw_str[maxn];
char str[maxn];
int  my_index[maxn];

/* 检查是否是字母 */
bool is_letter(char ch)
{
    return (ch >= 'A' && ch <= 'Z') || (ch >= 'a' && ch <= 'z');
}

/* 将大写字母转化为小写字母 */
char lower(char ch)
{
    if (ch >= 'A' && ch <= 'Z') {
        return ch + ('a' - 'A'); 
    }
    return ch;
}

int main()
{
    int max_len = 1, max_left = 0, max_right = 0, len = 0;

    cin.getline(raw_str, maxn, '\0');

    /* 处理原始输入，去掉非字母字符，将大写字母转为小写字母，并且建立处理前后下标的对应关系 */
    for (int i = 0; raw_str[i] != '\0'; i++) {
        if (is_letter(raw_str[i])) {
            my_index[len] = i;
            str[len] = lower(raw_str[i]);
            len++;
        }
    }
    str[len] = '\0';

    /* 查找回文字符串 */
    for (int i = 0; str[i] != '\0'; i++) {
        /* 奇数长度的情况 */
        int left = i - 1, right = i + 1;

        while (left >= 0 && right < len) {
            if (str[left] != str[right]) break;     // 非回文字符串，则跳出循环
            if (right - left + 1 > max_len) {       // 是回文字符串，判断是否超过了之前的最大长度
                max_len = right - left + 1;
                max_left = left;
                max_right = right;
            }
            left--;
            right++;
        }

        /* 偶数长度的情况，只是把left从i-1变为i,其余都没有改变 */
        left = i, right = i + 1;
        while (left >= 0 && right < len) {
            if (str[left] != str[right]) break;
            if (right - left + 1 > max_len) {
                max_len = right - left + 1;
                max_left = left;
                max_right = right;
            }
            left--;
            right++;
        }
    }

    /* 输出结果 */
    cout << max_right - max_left + 1 << endl;
    for(int i = my_index[max_left]; i <= my_index[max_right]; i++) {
        cout << raw_str[i];
    }
    cout << endl;

    return 0;
}
```

### 第5关：计算谐均值

```cpp
double Calculate(double x,double y)
{
	return 2 / (1 / x + 1 /y);
}
```

### 第6关：进制转换

```cpp
void printInt(int n, int base)
{
    char a[16] = {'0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'A', 'B', 'C', 'D', 'E', 'F'};
    char b[100] = {};
    int s = 0;
    while (n > 0) {
        b[s] = a[n % base];
        n /= base;
        s++;
    }
    for (int i = s - 1; i >= 0; i--) {
        cout << b[i];
    }
}
```