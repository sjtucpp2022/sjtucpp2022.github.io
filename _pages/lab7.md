---
title: 第7周上机：字符数组、函数
layout: post
---
### 1.统计元音字母个数
```cpp
#include <iostream>
using namespace std;
int main(){
    char a[81]={0};
    int count=0,i;
    cin.getline(a, 81);
    for(i=0;a[i]!='\0';i++){
        if(a[i]=='a'||a[i]=='e'||a[i]=='i'||a[i]=='o'||a[i]=='u'||a[i]=='A'||a[i]=='E'||a[i]=='I'||a[i]=='O'||a[i]=='U'){
            count+=1;
        }
    }
    cout<<"Count="<<count<<endl;

    return 0;
}
```

### 2.字符重排序
```cpp
#include <iostream>
using namespace std;
int main()
{
    int n=0, i, j;
    char a[81],temp;
    
    cin.getline(a,81);//长度为81的数组最多能存放80个字符

    for(i=0;a[i]!='\0';i++){ //统计字符长度
       n++;
   }
    for(i=0; i<n; i++){ //冒泡排序，每一轮把最小的放到0～n-1-i的最后
        for(j=0; j<n-i-1; j++){
            if(a[j]<a[j+1]){
                temp = a[j];
                a[j] = a[j+1];
                a[j+1] = temp;
            }
        }
    }

    //输出
    cout <<a[0];
    for(i=1; i<n; i++){
        if(a[i]!=a[i-1]) cout <<a[i];
    }


    return 0;
}
```

### 3.寻找字符串
```cpp
// 请在下方添加代码
/********** Begin *********/
#include <iostream>
using namespace std;
int main()
{
    char str1[161]={0},str2[161]={0};
    int i,j,t,loc=-1,s=0,l=0; //loc为str2首次出现的位置，s为str2长度，l为相同字符个数

    cin.getline(str1,161);
    cin.getline(str2,161);

    for(i=0;str2[i]!='\0';i++){
        s++;
    }

    for(i=0; str1[i]!='\0'; i++){ //用三层循环，第一层遍历字符串str1，第二层对于str1每一个位置的字符和str2对比，第三层遍历str2
        for(j=i; str1[j]!='\0'; j++){
            l=0; //每次遍历完相同的字符个数要置0
            for(t=0; str2[t]!='\0'; t++){
                if(str1[j+t]==str2[t])
                    l++;
            }
            if(l==s){
                loc=j;
                break;
            }
        }
        if(loc!=-1)
            break;
    }

    cout<<loc;

    return 0;
}
/********** End **********/
```

### 4.判断素数
```cpp
#include<iostream>
using namespace std;
bool isPrime(int n)
{
    /** Begin **/
    bool flag=false;
    int i;
    for(i=2;i<n;i++){
        if(n%i==0)
            flag=true;
    }
    if(!flag)return(1);
    else return(0);
    /**  End  **/
}

int main()
{
    int m, n,i,k=0;
    cin >> m >> n;
    
    /** Begin **/
    for(i=m; i<=n; i++){
        if(isPrime(i))
            k++;
    }
    if(m==1)cout<<k-1;
    else cout<<k;
    /**  End  **/
    return 0;
}
```
### 5.摩尔斯电码（附加题，选做）
```cpp
#include <iostream>
using namespace std;
int main(){
	char ori[100]={0};
	cin.getline(ori,100);
	char code[36][10]={
		{"-----"},{".----"},{"..---"},{"...--"},{"....-"},{"....."},
		{"-...."},{"--..."},{"---.."},{"----."},
		{".-"},{"-..."},{"-.-."},{"-.."},{"."},{"..-."},{"--."},{"...."},
		{".."},{".---"},{"-.-"},{".-.."},{"--"},{"-."},{"---"},{".--."},
		{"--.-"},{".-."},{"..."},{"-"},{"..-"},{"...-"},{".--"},{"-..-"},
		{"-.--"},{"--.."}
	};
	int i,j;
	char blank=' ';
	for(i=0;ori[i]!='\0';i++){
		if(ori[i] >= '0' && ori[i] <= '9'){
			cout<<code[i]<<' ';
		}	
	    else{
			if(ori[i] >= 'a' && ori[i] <= 'z'){
				if(ori[i+1]==blank) {
					cout<<code[ori[i]-'a'+10]<<"   "; //每个摩尔斯编码单词之间用三个空格
				}
				else cout<<code[ori[i]-'a'+10]<<' '; //每个摩斯码字母之间用一个空格
			}
			if(ori[i] >= 'A' && ori[i] <= 'Z'){
				if(ori[i+1]==blank) {
					cout<<code[ori[i]-'A'+10]<<"   ";
				}
				else cout<<code[ori[i]-'A'+10]<<' ';
			}

		}
	}
	return 0;
}
```
