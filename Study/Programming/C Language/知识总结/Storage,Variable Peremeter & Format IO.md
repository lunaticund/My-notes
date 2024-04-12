## 1.内存分配

### 1.1 <stdlib.h>

| 库函数 |  |
| --- | --- |
| void \*calloc(int num, int size); | 在内存中动态地分配 num 个长度为 size 的连续空间，并将每一个字节都初始化为 0。|
| void \*malloc(int num); | 在堆区分配一块指定大小的内存空间，用来存放数据。|
| void \*realloc(void \*address, int newsize); | 该函数重新分配内存，把内存扩展到 newsize。|
| void free(void \*address); | 该函数释放 address 所指向的内存块,释放的是动态分配的内存空间。 |
### 1.2 动态内存分配
根据需求来分配不同大小的内存
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main()
{
		char *str;
		str = malloc(200*sizeof(char));
		strcpy(str,"advertisment");
		printf("%s",str);
		free(str);
		return 0;
}
```
### 1.3 重新调整内存和内存的释放
当需要调整已分配内存的大小时，用`realloc()`函数。在某一块内存使用完后，用`free()`释放内存
## 2.变长参数
函数可根据需求接受不同数量的参数，例如`printf`,`scanf`等函数
### 2.1 声明
```c
int func(int arg1,...);
```
其中`…`表示可变参数列表，`…`前的参数是`int`，代表需要传递的参数个数。
例如
```c
int func(int, ... )  {
		...
}
 
int main() {
   func(2, 2, 3);
   func(3, 2, 3, 4);
}
```
### 2.2 <stdarg.h>
头文件`<stdarg,h>`提供了实现可变参数功能的函数和宏。

| 变量 |  |
| --- | --- |
| va_list | 适用于 va_start()、va_arg() 和 va_end() 这三个宏 |
| 宏 |  |
| void va_start(va_list ap, last_arg) | 初始化ap变量，arg是第一个传递进的参数。该宏将ap指向参数列表中第一个参数 |
| void va_start(va_list ap, last_arg) | 检索参数列表中下一个类型为type的参数。该宏返回类型为 type 的值，并将 ap 指向下一个参数。 |
| void va_end(va_list ap) | 结束可变参数列表的访问。该宏将 ap 置为 NULL。 |
### 2.3 功能实现
实现变长参数功能具体步骤：
1. 定义一个函数，最后一个参数为省略号，省略号前面可以设置自定义参数。
2. 在函数定义中创建一个**`va_list`**类型变量，该类型是在`<stdarg.h>`头文件中定义的。
3. 使用**`int`**参数和**`va_start()`**宏来初始化 **`va_list`**变量为一个参数列表。
4. 使用**`va_arg()`**宏和**`va_list`**变量来访问参数列表中的每个项。
5. 使用宏**`va_end()`**来清理赋予**`va_list`** 变量的内存。
例子：（求平均数）
```c
#include <stdio.h>
#include <stdarg.h>
 
double average(int num,...)
{
 
    va_list valist;
    double sum = 0.0;
    int i;
 
    /* 为 num 个参数初始化 valist */
    va_start(valist, num);
 
    /* 访问所有赋给 valist 的参数 */
    for (i = 0; i < num; i++)
    {
       sum += va_arg(valist, int);
    }
    /* 清理为 valist 保留的内存 */
    va_end(valist);
 
    return sum/num;
}
 
int main()
{
   printf("Average of 2, 3, 4, 5 = %f\n", average(4, 2,3,4,5));
   printf("Average of 5, 10, 15 = %f\n", average(3, 5,10,15));
}
```
再例如：（`printf()`的部分功能）
```c
void minprintf(char *fmt, ...)
{
	va_list ap; /* points to each unnamed arg in turn */
	char *p, *sval;
	int ival;
	double dval;
	
	va_start(ap, fmt); /* make ap point to 1st unnamed arg*/

	for (p = fmt; *p; p++) {
		if (*p != '%') {
			putchar(*p);
			continue;
		}
	/*查找需要输出的变量*/
		switch (*++p) {
			case 'd':
				ival = va_arg(ap, int);
				printf("%d", ival);
				break;
			case 'f':
				dval = va_arg(ap, double);
				printf("%f", dval);
				break;
			case 's':
				for (sval = va_arg(ap, char *); *sval; sval++)
					putchar(*sval);
				break;
			default:
				putchar(*p);
				break;
		}
	}

	va_end(ap); /* clean up when done */

	return;
}
```
## 3. 格式化输入输出
### 3.1 printf()标准输出

```c
printf("%+5d",4);//至少输出5个字符且把4放在最后位
输出结果："    4"

printf("%-5d",4);//至少输出5个字符且把4放在最前位
输出结果："4    "

printf("%05d",4);//至少输出5个字符，不足的用0补在前面
输出结果："00004"最前位

printf("%'d",100000);//每3位数字用"'"隔开
输出结果："100'000"

printf("%#d",4);//强制小数点
输出结果："4."
```
**返回值**：`printf()`返回输出字符的个数，当出现错误时返回负值
### 3.2 scanf()标准输入
**返回值**：`scanf()`返回成功转化的个数，不包括只读的字符或空格
严格区分`%f`和`%lf`
一个空格，`\t`，`\n`可以匹配多个空格，其他字符必须严格匹配
`%*d`：只扫描不读取（跳过一个数）