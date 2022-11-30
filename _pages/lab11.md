## 1.时钟结构体
```
#include <iostream>
using namespace std;

struct electronicClock {
	int hour, minute, second;
	void setTime(int h, int m, int s) {
    	// write your code here
        hour=h;
        minute=m;
        second=s;
        
    }
    void increase() {
    	// write your code here
        second+=1;
    	if(second>=60){
    	   second-=60,minute+=1;
    	   if(minute>=60){
    	   	minute-=60,hour+=1;
			   if(hour==24) hour=0;
		   }
		}
        
    }
    void showTime() {
    	// write your code here
        int sec[2];
    	sec[0]=second/10;
    	sec[1]=second%10;
    	int min[2];
    	min[0]=minute/10;
    	min[1]=minute%10;
        int hr[2];
    	hr[0]=hour/10;
    	hr[1]=hour%10;
    	cout<<hr[0]<<hr[1]<<":"<<min[0]<<min[1]<<":"<<sec[0]<<sec[1]<<endl;
        
    }
};
int main(){
	electronicClock clk;
    
    for (int t=0; t<2; t++) {
    	int h, m, s;
        cin >> h >> m >> s;
        clk.setTime(h, m, s);
        clk.showTime();
        clk.increase();
        clk.showTime();
    }
	
	return 0;
}
```
## 2.有理数化简
```
#include <iostream>
using namespace std;

struct rationalNumber{
    int fenzi; // 分子
    int fenmu; // 分母
};

// 函数reduction：有理数化简，对传入的有理数n进行化简
// 参数：n-有理数
// 返回值：无化简后的有理数
rationalNumber reduction(rationalNumber n);

int main()
{
    char c;
    rationalNumber x, y;
    cin >> x.fenzi >> c >> x.fenmu;   // 输入有理数，首先读入分子，然后是/，最后是分母
    y = reduction(x);   // 有理数化简
    // 输出化简的结果
    if(y.fenmu == 1)
        cout << y.fenzi << endl;
    else
        cout << y.fenzi << "/" << y.fenmu << endl;
    return 0;
}

rationalNumber reduction(rationalNumber n)
{
    // 请在这里补充代码，实现函数reduction
    /********** Begin *********/
    int flag = 1,k;
    if(n.fenzi == 0)
    {
        n.fenmu = 1;
        return n;
    }
    if(n.fenzi < 0)
    {
        n.fenzi = -n.fenzi;
        flag = -1;
    }
    k = (n.fenmu > n.fenzi) ? n.fenzi : n.fenmu;
    while(k > 1)
    {
        if(n.fenmu % k == 0 && n.fenzi % k == 0)
        {
            n.fenmu = n.fenmu / k;
            n.fenzi = n.fenzi / k;
        }
        k--;
    }
    n.fenzi = n.fenzi * flag;
    return n;
    
    
    /********** End **********/
}
```
## 3.英雄排序
```
#include <iostream>
using namespace std;
struct hero{
	string name;
	int age;
	string sex;
};

int main(){
	struct hero harry[5];
	for(int i=0;i<5;i++){
			cin>>harry[i].name>>harry[i].age>>harry[i].sex; 
		}
		for(int i=0;i<4;i++){
			for(int j=0;j<5-i-1;j++){
				if(harry[j].age>harry[j+1].age){
				hero temp=harry[j];
				harry[j]=harry[j+1];
				harry[j+1]=temp;
				}
			}
		}
	for(int i=0;i<5;i++){
			cout<<harry[i].name<<" "<<harry[i].age<<" "<<harry[i].sex<<endl; 	
   }
}
```
## 4.复数结构体
```
#include <iostream>
using namespace std;
struct ComplexNum{
    int a,b;
    void sum(ComplexNum X,ComplexNum Y){
        a = X.a + Y.a;
        b = X.b + Y.b;
    }
    void times(ComplexNum X, ComplexNum Y){
        a = X.a * Y.a - X.b * Y.b;
        b = X.b * Y.a + X.a * Y.b;
    }
    void display(){
        cout << a;
        if (b > 0) cout << '+';
        cout << b << 'i' << endl;
    }
}x,y,m,n;

int main(){
	int a,b,c,d;
    cin >> a >> b >> c >> d;

    x.a = a; x.b = b; y.a = c; y.b = d;

    cout << "x = "; x.display();
    cout << "y = "; y.display();
    x.sum(x,y);
    cout << "x += y; x = "; x.display();
    y.times(x,y);
    cout << "y *= x; y = "; y.display();
    
    m.sum(x,y); n.times(y,x);
    cout << "x + y = "; m.display();
    cout << "y * x = "; n.display();

    cout << "x = "; x.display();
    cout << "y = "; y.display();
	return 0;
}
```
