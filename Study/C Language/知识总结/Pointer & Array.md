## 1.Pointer
**The Pointer and Address**
&：取地址，can't be applied to **expressions**,**constants** and **register variables**
\*：作用于一个地址时，表示地址指向的object
**The Pointer and Function Call**
通过地址，可在函数内部改变函数外部的变量
注意：函数形参为pointer时，实参要用”&“取地址

一些指针定义的易错点：
```c
int * p = &a;
int  * * q = &p;//q是pointer，指向的object也是pointer

int*      x,y;//x是pointer，y是integer
```
## 2.The Array and Pointer
任何数组能完成的操作，指针都能完成
数组相较于指针更加直观
```c
int a[10];
int *p;
p=&a[0];p=a;//两者结果相同

p=&a[5];//*p++ = *(p++) = a[6]
```
一些特例：
```c
int *q[10];
//q是一个数组，每个元素都是一个指针，每个指针指向一个int
```
```
int q[]={1,2,3};
sizeof(q)//3*sizeof(int)
sizeof(*q)//=sizeof(q[0])=sizeof(int)
```
```c
int a[]={1,2,3,4,5};
int *p;
p=a+5;//越界
p[-1]=6;//a[4]=6
```
一个例子：
```c
void swap(int *a,int *b)
{
	int temp;
	temp=*a;
	*a=*b;
	*b=temp;
}
int main(void)
{
int a=3,b=4;
swap(&a,&b);//需要"&"取地址

int q[]={1,2,3};
swap(q,q+1);//数组名本身是一个地址常量
swap(q,0,1);//相当于swap(q+0,q+1)
return 0;
}
```
## 3.Character Pointers and Functions
```c
int message[] = "I am here.";//message为一个数组，每个字符为它的一个元素
int *pmessage = "I am here."//pmessage为指针，指向"I am here."这个字符串
```
**第一种可写，第二种不可写**
下面是一个用指针优化程序的例子：
```c
void strcpy(char *s, char *t)
{
	int i;
	i = 0;
	while ((t[i] = s[i]) != '\0')\\字符串以'\0'结尾
	i++;
}
```
优化为：
```c
void strcpy(char *s, char *t)
{
	while ((*t = *s) != '\0'){
	t++;
	s++;}
}
```
更进一步：
```c
void strcpy(char *s, char *t)
{
	while ((*t++ = *s++) != '\0'){
	;}
}
```
判断条件为“$\neq 0$”时可省略，即：
```c
void strcpy(char *s, char *t)
{
	while(*t++ = *s++) 
	;
}
```
## 4.Pointer Arrays, Pointers to Pointers
```c
int * p[3];//p是一个有3个元素的数组，每个元素是一个指针
int a1[]="before",a2[]="now",a3[]="after";
p[0]=a1;
p[1]=a2;
p[2]=a3;
```

```c
int * *p;//p是一个指针，且指向一个指针
int b=3;
*p = &b
```
*在实际问题中进行应用*
## 5.Multi-dimensional Array
**定义**：
```c
type name [length1][length]
```
例：
```c
int martix[2][5];//martix是一个有2个元素的数组，每个元素是有5个元素的数组
同理
int array[2][3][4];
```
当一个函数以一个多维数组为参数时，只有第一个长度可不写
```c
f(int daytab[2][13]) { ... }
f(int daytab[][13] ) { ... }
f(int (*daytab)[13]) { ... }
// not equal to : 
f(int *daytab[13] ) { ... }//相当于f(int * *daytab){}
```
一些易错点：
1. 
```c
int a[2][3];
int *p;
p=a[0]//p指向a[0][0]的地址
```
2. 
`int (*q)[3];`q是一个指针，指向有3个元素的int类型数组
`q=a;`
3. 
在(1)的基础上，如果
`p=a;`
则会进行强制类型转换：a\[\ \]->int \*a
4. 
`a[2][-1]==a[1][3];`
5. 
`int a[][3]`可以
`int a[2][]`不可以
即只能数最外面的个数
6. 
```c
int a[2][3][4][5];
int (*p)[5];
p=a[0][0];
```
7. 
注意区分
`int (*a)[10]`和`int *a[10]`
## 6.Initialization of Pointer Array
```c
static char *name[] = {
	"Illegal month",
	"January", "February",
	"March", "April",
	"May", "June",
	"July", "August",
	"September", "October",
	"November", "December"
};//每个元素都是指向对应字符串的指针
```
## 7.Pointers vs. Multi­dimensional Arrays
```c
char *name[] = { "Illegal month", "Jan", "Feb", "Mar" };
char aname[][15] = { "Illegal month", "Jan","Feb", "Mar" };
```

## 8.Command-line Argument
从命令行传值给程序，可以从外部控制程序。
```c
int main( int argc, char *argv[] )
```
命令行参数是使用 main() 函数参数来处理的，其中，`argc` 是指传入参数的个数，`argv[]` 是一个指针数组，指向传递给程序的每个参数。
**argv\[0\]** 存储程序的名称，**argv\[1]** 是一个指向第一个命令行参数的指针，\*argv\[n] 是最后一个参数。如果没有提供任何参数，argc 将为 1，否则，如果传递了一个参数，**argc** 将被设置为 2。
多个命令行参数之间用空格分隔，但是如果参数本身带有空格，那么传递参数的时候应把参数放置在双引号  " "  或单引号  ' '  内部。
## 9.Pointers to Functions
函数名的估值也是一个地址
我们可以使用指针去调用函数
```c
声明：
int (*fun_ptr)(int,int);//包括函数的参数类型和返回值类型
调用：
fun_ptr(a,b);//或(*fun_ptr)(a,b)
```
我们可以将数组与函数指针结合起来
```c
int (*q[2])(int,int)={fun1,fun2};
```
函数可以返回函数（指针）
回调函数：函数的参数可以是函数函数指针

## 10.Complex Declaration
通过pointer array,pointer to pointer,pointer to function等等，我们可以实现很复杂的运算。下面是一些comlicated declaration
```c
char (*(*x())[])();
char (*(*x[3])())[5];
```