## 程序
```
#include<iostream>
#include<string>
#include <limits>
using namespace std;
int main()
{
    cout << "type: \t\t\t" << "************size**************"<< endl;
    cout << "short: \t\t\t" << "字节数：" << sizeof(short) <<endl;
    cout << "最大值：" << (numeric_limits<short>::max)();
    cout << "\t\t最小值：" << (numeric_limits<short>::min)() << endl;
    cout << "int: \t\t\t" << "字节数：" << sizeof(int) <<endl;
    cout << "最大值：" << (numeric_limits<int>::max)();
    cout << "\t最小值：" << (numeric_limits<int>::min)() << endl;
    cout << "unsigned: \t\t" << "字节数：" << sizeof(unsigned) <<endl;
    cout << "最大值：" << (numeric_limits<unsigned>::max)();
    cout << "\t最小值：" << (numeric_limits<unsigned>::min)() << endl;
    cout << "long: \t\t\t" << "字节数：" << sizeof(long) <<endl;
    cout << "最大值：" << (numeric_limits<long>::max)();
    cout << "\t最小值：" << (numeric_limits<long>::min)() << endl;
    cout << "unsigned long: \t\t" << "字节数：" << sizeof(unsigned long) <<endl;
    cout << "最大值：" << (numeric_limits<unsigned long>::max)();
    cout << "\t最小值：" << (numeric_limits<unsigned long>::min)() << endl;
	cout << "long long: \t\t" << "字节数：" << sizeof(long long) <<endl;
    cout << "最大值：" << (numeric_limits<long long>::max)();
    cout << "\t\t最小值：" << (numeric_limits<long long>::min)() << endl;
	cout << "unsigned long long: \t" << "字节数：" << sizeof(unsigned long long) <<endl;
    cout << "最大值：" << (numeric_limits<unsigned long long>::max)();
    cout << "\t\t最小值：" << (numeric_limits<unsigned long long>::min)() << endl;
    cout << "double: \t\t" << "字节数：" << sizeof(double) <<endl;
    cout << "最大值：" << (numeric_limits<double>::max)();
    cout << "\t最小值：" << (numeric_limits<double>::min)() << endl;
    cout << "long double: \t\t" << "字节数：" << sizeof(long double) <<endl;
    cout << "最大值：" << (numeric_limits<long double>::max)();
    cout << "\t最小值：" << (numeric_limits<long double>::min)() << endl;
    cout << "float: \t\t\t" << "字节数：" << sizeof(float) <<endl;
    cout << "最大值：" << (numeric_limits<float>::max)();
    cout << "\t最小值：" << (numeric_limits<float>::min)() << endl;
    return 0;
}
```
## 运行结果
```
type:                   ************size**************
short:                  字节数：2
最大值：32767           最小值：-32768
int:                    字节数：4
最大值：2147483647      最小值：-2147483648
unsigned:               字节数：4
最大值：4294967295      最小值：0
long:                   字节数：8
最大值：9223372036854775807     最小值：-9223372036854775808
unsigned long:          字节数：8
最大值：18446744073709551615    最小值：0
long long:              字节数：8
最大值：9223372036854775807             最小值：-9223372036854775808
unsigned long long:     字节数：8
最大值：18446744073709551615            最小值：0
double:                 字节数：8
最大值：1.79769e+308    最小值：2.22507e-308
long double:            字节数：16
最大值：1.18973e+4932   最小值：3.3621e-4932
float:                  字节数：4
最大值：3.40282e+38     最小值：1.17549e-38
```
