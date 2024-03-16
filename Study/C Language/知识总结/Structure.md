## 1.Structure
#### 1.The Definition of Structure
结构是一种新的数据类型，将有内在联系的数据组合成一个整体
结构中的成员都是不同类型的变量（int，double，指针，数组$\cdots$）
**结构的定义**：
```c
struct tag { 
    member-list
    member-list 
    member-list  
    ...
} variable-list ;
```
`struct`与后面的结构名`tag`共同构成一个新的变量类型
例：
```c
struct student{
	int num;
	char name[10];
	int math,English,physics
	double aver;
};//这个结构包括学生学号，姓名，成绩等数据
```

**structure的padding**：（内存管理）对结构中连续存放的数据，第一个数据从0地址（即初始位置开始），之后的数据存放地址必须与自己的长度对齐
例如：`int`长度为4，则其地址必须为4的倍数，`double`必须为8的倍数
可以利用`#pragma pack`规定最大的对齐位
例如：`#pragma pack 2`则即使是`int`，其地址也只能按2的倍数对齐
对齐会直接影响structure的长度
```c
struct {
    int i;
    char c1;
    char c2;
} x1;
```
上例中`x1`的长度为8
#### 2.Nesting Definition
结构中的成员是不同类型的数据，而已定义的结构也是一种数据类型，所以在定义结构时可以包含已定义的结构类型的变量
例：
```c
struct address{
	char city[50];
	char street[50];
}
struct student{
	int num;
	char name[10];
	struct address addr;
	int math,English,physics
	double aver;
};//address作为单独的结构定义
```
数据封装：将强关联的数据单独封装为一个结构，利于数据的分析和处理
#### 3.The Definition and Initializtion of Structure Variable
与一般的变量定义相同
```c
sturct student wenji;//单独定义

struct student{
	int num;
	char name[10];
	int math,English,physics
}wenji,zhaoyu;//在定义结构类型时同时定义变量

struct {
	int num;
	char name[10];
	int math,English,physics
}wenji;//无结构名定义,在定义之后则不可再定义变量（除非再写一次结构定义）
```
初始化
```c
sturct wenji = {323,"wenji",135,90,110};
```
#### 4.References to Structure Members
使用操作符" . "来引用结构成员
```c
	wenji.num=323;
	wenji.name="wenji";
```
对嵌套结构的成员的引用
```
struct student stu;
stu.addr.city = "Hangzhou"
```
从外向力依次引用
相同类型的结构变量可以通过"="整体赋值，即把右侧的变量完全拷贝给左侧
**结构变量作为函数的参数**
```c
int func(int num1,char name[]);
func(stu.num,stu.name);//传入参数可以是单独的结构成员

int func(struct student stu1);
func(stu);//传入参数可以是整个结构
```
同时结构也可以作为函数返回值
当结构作为参数或返回值是，对于大型结构，会使得数据的复制效率很低
所以对于大型结构，我们采用指针进行传递
#### 5.Structure Array&Pointer to Structure
**1. Structure array:**
```c
struct student stu[20];//长度为20的数组,每个元素都是一个结构（20个学生的信息）
```
初始化：
```c
struct student stu[20] = {{3231,"wenji",150,134,109},{3232,"xilai",···}···}；//内部的{}可省略
```
结构成员的引用：
```c
stu[2].num;
```
所有元素属于相同的类型，可以直接赋值
**2. Pointer to structure**
```c
//declaration
struct student *p;
//赋值
p = &wenji
```
利用指针调用结构成员：
```c
(*p).num = 323;
p->num = 323;
//两者效果相同
```
访问结构成员的两种运算符"`.`"和"`->`"有最高的优先级
**必考**：当指针、数组、结构结合在一起时对于一个复杂的表达式，根据优先级找到其指向的位置
再次强调指针指向的字符串是**read only**
利用结构指针可以实现结构自指和结构的互指，即可形成单链表、双链表、环链表

**下面是两个易错点**：
1.匿名结构：即在一个结构中定义另一个没有名称的结构
```c
#include <stdio.h>

struct point {
    struct {
        int x;
        int y;
    };//定义了匿名结构
};

int main() {
    struct point p;
    p.x = 10;
    p.y = 20;
    printf("The point is at (%d, %d)\n", p.x, p.y);
    return 0;
}
```
在上述例子中，我们可以通过`p.x,p.y`直接引用匿名结构中的成员
2.无尺寸数组成员：即零长度数组，这种成员在结构中不占用内存，指是一个地址常量。无尺寸数组成员必须定义在结构体里面且为最后元素；结构体中不能单独只有无尺寸数组成员
```c
struct soft_buffer  
{  
  int len;  
  char data [0];  
};
```
例如`data`是一个无尺寸数组，在定义`struct soft_buffer`类型的变量时，可动态的为`data`分配内存
## 2.typedef
#### 1.Effect of typedef
利用`typedef`可以给数据类型取一个别名
例：
```c
typedef int* PINT;
typedef int[20] arr[20];
//在此之后即可用PINT去定义int*型的变量
int a=10;
PINT p=&a;
//一个坑点：不能简单的把PINT换成int*去理解，如：
PINT p,q;//p,q都是指针
```
我们也可用`typedef`去给自定义的数据类型（结构，枚举等）取别名
```c
typedef struct student{
	int num;
	char name[10];
	int math,English,physics
	double aver;
}STU;//之后就可以STU去定义结构变量
STU wenji;
```
#### 2.typedef vs. \#define
\#define是预处理指令，可以给各种数据定义别名
- **typedef** 仅限于为类型定义符号名称，**#define** 不仅可以为类型定义别名，也能为数值定义别名，比如您可以定义 1 为 ONE
- **typedef** 是由编译器执行解释的，**#define** 语句是由预编译器进行处理的
## 3.Union
union：一种数据结构，允许在相同的储存位置储存不同数据类型的变量
#### 1.Definition
```c
union [union tag]
{
   member definition;
   member definition;
   ...
   member definition;//标准变量定义（固定或自定义）
} [one or more union variables];
```
union内存为member中最大的内存，例
```c
#include <stdio.h>
#include <string.h>
 
union Data
{
   int i;
   float f;
   char  str[20];
};
 
int main( )
{
   union Data data;        
   printf( "Memory size occupied by data : %d\n", sizeof(data))；
   return 0;
}//结果Memory size occupied by data : 20
```
#### 2.Reference to Union Member
与structure的reference相同，使用" . "进行引用
注意：当引用union中不同的变量时，会造成数据的覆盖。例：
```c
#include <stdio.h>
#include <string.h>
 
union Data
{
   int i;
   float f;
   char  str[20];
};
 
int main( )
{
   union Data data;        
 
   data.i = 10;
   data.f = 220.5;
   strcpy( data.str, "C Programming");
 
   printf( "data.i : %d\n", data.i);
   printf( "data.f : %f\n", data.f);
   printf( "data.str : %s\n", data.str);
 
   return 0;
}
```
所以，在使用union时，同一时间只能使用一个变量
union可用来判断机器是大端机还是小端机
```c
union
{
    char str;
    int data;
};
data=0x01020304;
if(str==0x01)
{
    cout<< "此机器是大端！"<<endl;
}
else if(str==0x04){
    cout<<"此机器是小端！"<<endl;
}
else{
    cout <<" 暂无法判断此机器类型！"<<endl;
}
```
当处理两个很大的结构时，利用union可节省内存