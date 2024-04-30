# luogu 数据生成利器

## gen

`gen.exe` 是生成数据的随机数工具，一般由题目的要求进行数据生成。

随机数 `rand()`。

`rand()` 可以被理解成一个变量，需要在主函数进行随机种子操作 `srand(time(0))`。

`rand() % 10` 可以理解成 $0 \sim 9$​ 区间的随机数。

贴一个示例 `gen.exe` 文件。

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
	ios::sync_with_stdio(0);
	cin.tie(0);
	srand(time(0));
	int n = 100000, q = 99999, r = rand() % 5000, k = rand() % 100;
	cout<<n<<" "<<q<<" "<<k<<" "<<r<<"\n";
	for(int i = 1;i <= n;i++){
		cout<<rand() % 5<<" \n"[i == n];
	}
	for(int i = 1;i <= n;i++){
		cout<<rand() % 50<<" \n"[i == n];
	}
	for(int i = 1;i <= q;i++){
		cout<<n-i<<"\n";
	}
	cout<<100000<<"\n";
	return 0;
}
```

## test

`test.exe` 是指标准程序，不能出错。一般把 `gen` 和 `test` 放在一起。

示例 `test`。

```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
    int a,b;
    cin>>a>>b;
    cout<<a+b;
    return 0;
}
```

## 数据生成

先贴代码：

```cpp
#include <bits/stdc++.h>
using namespace std;

void printf_green(const char *s)
{
	printf("\033[0m\033[1;32m%s\033[0m\n", s);
}

int main(){
	
	for(int i = 1;i <= 100;i++){// 数据范围 
		
		string str = to_string(i);
		while(str.size() < 3){
			str = "0" + str;
		}
		string aa = "gen > " + str + ".in.txt";
		string bb = "test.exe < " + str +".in.txt > " + str + ".out.txt";
		string ct = "OK on test " + str;
		const char* cc = nullptr;
		const char* dd = nullptr;
		const char* ct1 = nullptr;
		cc = aa.c_str(), dd = bb.c_str(), ct1 = ct.c_str();
		system(cc);
		system(dd);
		printf_green(ct1);
	}
	
	return 0;
}
```

其中，第六行的 `for` 循环，表示在同一个 `gen` 的情况下数据生成个数。

第 $9$ 行的 `while` 循环，意在把数字补前导 $0$。

