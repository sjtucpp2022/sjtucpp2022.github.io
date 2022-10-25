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

