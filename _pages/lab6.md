---
title: 第六周上机：数组
layout: post
---

# 第6周上机：
## 1.第一次和最后一次
```cpp
#include<iostream>
using namespace std;
int main() 
{
    int n,x,i,first=-1,last=-1;
    cin >>n;
    int a[n];
    for(i=0;i<n;i++){
        cin >>a[i];
    }
    cin >>x;

    for(i=0;i<n;i++){
        if(a[i]==x){
            if(first==-1){
                first=i;//first只赋值1次，每找到一次目标值更新一次last
            }
            last=i;
        }
    }
    cout <<first<<' '<<last;

  return 0;
}
```

## 2.1的个数
```cpp
#include<iostream>
using namespace std;
int main() 
{
    int n,i,j,flag=0;
    cin >>n;
    int a[n][n],b[n];//b[n]存放每一行1的个数
    for(i=0;i<n;i++){
        for(j=0;j<n;j++){
            cin >>a[i][j];
        }
    }

    for(j=n-1;j>=0;j--){
        for(i=0;i<n;i++){
            if(a[i][j]==1){
                cout << i;
                flag=1;
                break; //找到1最多的行跳出内层循环
            }
        }
        if(flag==1)
            break;//跳出外层循环
    }


  return 0;
}
```

## 3.改错题-二维数组
```cpp
#include <iostream>
using namespace std;
const int MAX_SIZE = 10;
int main(){
    int i, j, m, n, x;
    int mat[MAX_SIZE+1][MAX_SIZE];

    // cout<<"Please input m, n:";
    cin>>m>>n;
    // cout<<"Input array:\n";
    for(i = 0; i<m; i++){ //输入矩阵
        for(j = 0; j<n; j++){
            cin>>mat[i][j];
        }
    }

    // for(i = m-1; i>0; i--){
    //     for(j = 0; j<n; j++){
    //         mat[(i+1)%m][j]=mat[i][j];
    //     }
    // }
    for (i = m - 1; i > 0; i--) {
        for (j = 0; j < n; j++) {
            x = mat[(i - 1) % m][j]; mat[(i - 1) % m][j] = mat[i][j]; mat[i][j] = x;
        }
    }

    // cout<<"New array:\n";
    for(i = 0; i<m; i++){
        for(j = 0; j<n; j++){
            cout<<mat[i][j]<<'\t';
        }
        cout<<endl;
    }
    return 0;
}
```

## 4.寻找鞍点-二维数组
```cpp
#include<iostream>
using namespace std;
int main() {
	int m, n, mat[10][10] = { 0 }, i, j, x, y;
	bool flag = 0, flag2 = 0;
	cin >> m >> n;
	for (i = 0; i < m; i++)
	{
		for (j = 0; j < n; j++)
			cin >> mat[i][j];
	}
	for (i = 0; i < m; i++)
	{
		for (j = 0; j < n; j++)//对每一个元素进行判断
		{
			flag = 0;
			for (x = 0; x < n; x++)
			{
				if (mat[i][j] < mat[i][x])
				{
					flag = 1; break;
				}                    //行判断，如果不符合直接结束
				if (flag) break;       
				else {                 
					for (y = 0; y < m; y++)      //进行列判断
					{
						if (mat[i][j] > mat[y][j])
						{
							flag = 1; break;
						}
					}
				}
			}
			if (!flag)
			{
				cout << "mat[" << i << "][" << j << "]=" << mat[i][j] << endl; flag2 = 1;
			}
		}
	}
	if (!flag2) cout << "Not Found" << endl;
	return 0;
}
```

## 5.插入排序
```cpp
#include<iostream>
using namespace std;
int main() {
	int n, i, j, a[100] = { 0 }, t;
	cin >> n;
	for (i = 0; i < n; i++) //输入数组
		cin >> a[i];

	for (i = 1; i < n; i++)      //便利数组从1~n-1
	{
        for(j=i-1;j>=0;j--){ //和前i-1个数进行比较，如果比前一个数小，互换位置
            if(a[j+1]<a[j]){
            t = a[j];
            a[j] = a[j+1];
            a[j+1] = t;
            }
        }
	}
	for (i = 0; i < n; i++)
	{
        cout << a[i] <<' ';
	}

	return 0;	
}
```

## 6.数字金字塔-二维数组
```cpp
#include<iostream>

using namespace std;
int main()
{
    int a[100][100] = {0}; //输入的金字塔
    int max=0; //路径最大值

    int n, i, j, k;
    cin >> n;
    for (i = 0; i < n; i++) //输入金字塔
        for (j = 0; j <= i; j++)
            cin >> a[i][j];

    for(i=1; i<n; i++){ //更新金字塔，金字塔每个位置保存经过该路径数字最大和
        for(j=0; j<=i; j++){
            if(j==0)
                a[i][j] =a[i][j] + a[i-1][j];
            else
                a[i][j] = a[i][j] + (a[i-1][j]> a[i-1][j-1]?  a[i-1][j]:a[i-1][j-1]);
        }
    }
 
    for(i=0; i<n; i++){
        if(a[n-1][i]>max)
            max = a[n-1][i];
    }    
    cout << max << endl;

    return 0;
}
```
