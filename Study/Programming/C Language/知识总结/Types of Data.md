## 1.变量类型
##### 1.1整数
- char:1~byte$\quad$ short:2~bytes$\quad$ int:4~bytes$\quad$ longlong:8~bytes
- unsigned:无符号$\quad$ signed：有符号
- 十进制：首位不为0  $\quad$八进制：首位为0，各位不大于7$\quad$十六进制：0x开头，各位0~f
- 后缀u或U，l或L
##### 1.2字符类型
- 可以用整数直接来表示字符
- 整数和字符变量的定义和值都可以相互交换
- 字符具有数值特征，可以进行计算。如'A'+1='B'
- 转义字符：\\t, \\n, \\\\,  \\", \\', \\ddd(八进制整数代表的字符 \\102='B'), \\xhh(十六进制整数代表字符 \\x41='A')

**字符串常量**
"abc"
字符串常量本质是指针（估值）
1. 字符串常量可以看作一个元素为字符的数组
2. 在内存中存储字符串时，结尾有'\\0'
3. 区分一个字符 'x' 和只包含但个字符的字符串 "x"
##### 1.3浮点数
float：单精度，4bytes，有效位数7~8位，取值范围$\pm (10^{-38}-10^{38})$
double；双精度，8bytes，有效数位15~16位，取值范围$\pm(10^{-308}-10^{308})$
表示浮点数必须带小数点
科学计数法：e之前要有数据，e之后要为整数
##### 1.4变量类型转换
**自动类型转换**
计算式规律：将小的转化为大的，将signed转化为unsigned
赋值将赋值号右侧类型自动转化为左侧类型
故左值级别低时，可能导致数据失真或精度降低（如float$\rightarrow$int  *会给warning*）

**强制类型转换**
（类型名）表达式
如(double) i表示将i转化为double类型

**类型转换是临时性的，没有改变变量类型的定义，不会保存到记忆中**
##### 1.5变量的输入输出
**整数类型**

|格式|%d|%u|%o|%x|
|-------|-----|----|----|----|
|含义|十进制|十进制无符号|八进制|十六进制|
输出长类型时，要加 $l$ 前缀

**浮点数类型**

|函数|格式|
|---|---|
|printf|%f(小数形式)，%e(指数形式)|
|scanf|%f或%e(单精度)，%lf或%le(双精度)|
*输入long或double时必须有l限定*
输出时可以指定输出宽度

**字符类型**
可以采用 getchar( ) , putchar( ) , scanf( ) , printf( )
其中 getchar( ) putchar( ) 只能处理单个字符的输入输出
scanf，printf 可处理多个字符
注意：输入多个字符时，字符之间的间隔符也会被识别
## 2.枚举类型（enum）
##### 定义
枚举类型：在实际问题中，有些变量的取值被限定在一个有限的范围内，通过枚举类型列出所有可能的取值。（如一年12个月，一天24个小时）
定义：
```c
enum 枚举名
{
	枚举变量表
};
```
例如：
```c
enum week
{
	Mon,Tues,Wed,Thurs,Fri,Sat,Sun
}//不写对应的值，则默认从0开始。也可自定义取值
```
枚举类型变量：
```c
enum weekday{sun,mon,tue,wed,thu,fri,sat};  //定义枚举类型
enum weekday a,b,c;                         //定义3个枚举类型的变量
enum weekday{sun,mon,tue,wed,thu,fri,sat}a,b,c; //定义枚举类型的同时，定义3个变量
enum{sun,mon,tue,wed,thu,fri,sat}a,b,c;     //枚举名可省略，但后面不能再定义新的枚举变量
```
用 typedef 定义枚举变量的别名：
```c
typedef enum weekday        //此处的weekday为枚举名，可省略
{
    Mon = 0,Tues,Wed,Thurs,Fri,Sat,Sun
}weekday;               //此处的weekday为enum weekday的别名

weekday today, tomorrow;        //枚举类型的变量，即enum weekday类型
```
注意：不能定义同名枚举别名，不同枚举变量不能包含相同元素

