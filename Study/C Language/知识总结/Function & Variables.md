## 1.函数
##### 1.函数的作用
1. 功能分割：将大任务分割成几个小任务分别执行
2. 功能封装：将一个具体的功能封装为一个函数（如isPrime），从而我们可以直接调用函数，而不许要知道其中的具体操作
3. C语言使得函数的使用更加方便和高效
##### 2.函数的声明和定义
定义的形式如：
```
函数类型 函数名（形参）
{
	函数主体
}
```
声明为：
$$int~isPrime(int~x);$$
注：
1. 函数在调用前必须先声明
2. 函数可以在函数内部声明，但不能在内部定义
##### 3.函数的参数
```c
int func(int x,int y)    //此处 x,y 均为形式参数
{
	x++,y--;
	return x+y;
}
int main(void)
{
	int a=1,b=2;
	int c=func(a,b);    // a,b 为实际参数
	printf("%d",c);
	return 0;
}
```
1. 参数的类型可以是变量的任何类型
整数，浮点数，指针（指针变量传递时要用 “&” 取地址）
2. 参数的定义与变量定义相同
3. C语言函数是call-by-value，即实际参数只将自己的数值传递给形式参数
##### 4.函数返回值
返回值可以是任何basic-type：整数，浮点数，结构，void
## 2.变量
##### 1.外部变量（external variable）
external objects:external variables & functions
1. 外部变量定义在函数外，可在多个函数中使用
2. 函数都是外部的（C不允许函数定义在函数内）
3. 外部变量是在不同函数之间传递数据的一种手段
4. 在声明了外部变量名后，任何函数都可直接使用（仍需先声明）
例：
```c
a.c
int a = 10;

b.c
#include<stdio.h>
#include"a.c"
int main(void)
{
	printf("%d",a);   //因为包含了 a.c 文件，所以可直接使用
	return 0;
}
```
##### 2.自动变量（internal variable）
自动变量：定义在函数内部，进入函数时生成，离开函数时消失
反之，外部变量时permanent，不随进出函数改变数值
##### 3.作用范围（scope）
scope：即变量可以被使用的范围
**自动变量**：在变量定义的函数之中 
注：*不同函数中定义的同名自动变量没有关系*

**外部变量和函数**：从declaration到编译的文件结束
1. declaration$\neq$definition:
declaration:告知变量的属性（primarily the type）
definition:除了属性，还定义了储存位置
2. 一个外部变量只在一个文件中有定义，但在其他用到它的文件的要有声明
`external int x`
##### 4.静态变量（static variable）
1. apply to an external variable：表明此变量只在其声明的文件中作用。
可用函数封装静态变量，则其可在外部文件中调用
2. apply to an internal variable：相当于一个外部变量（不随进出函数而产生或消失（栈始终存在），初始化只在第一次有用），但其作用用范围只在其声明的函数内
```c
int f()
{
	static int a=100;
	a=a++;
	return a;
}//a的值不再随进入f而每次赋为100
```
3. apply to a function：静态函数，不可被外部文件调用
##### 5.寄存器变量（register variable）
储存分为内存和寄存器，将常用变量存在寄存器中，可以让程序运行更快
寄存器变量不能取地址
1. register can only be applied to automatic variable
2. "register" is only an suggestion,and compilers are free to ignore it
##### 6.变量初始化（initialization）
1. 对于外部和静态变量，初始化必须是constant expression，需要在程序执行前初始化。若无初始化，则自动保存为0
2. 对自动变量，初始化可以包括先前定义的变量，或function call

## 两点补充
##### 变量储存的内存分布
C语言将变量的数据区分为动态储存区和静态储存区
- 静态储存区：储存全局变量和静态变量，程序执行时一直存在
- 动态储存区：进入一个函数时生成一个栈，用以储存函数中的自动变量，离开函数时栈消失
##### 递归函数
通过自己调用自己或者两个函数相互调用来实现
1. 要设置出口，即在满足一定条件时离开递归
2. 注意在函数中调用函数的位置，决定了程序执行的顺序
3. 递归函数容易理解，但代价较大。一般递归函数可转化为非递归程序
