## 1.变量
FILE：用于储存文件流信息的变量
fpos_t：适用于保存文件任何位置
## 2.宏
NULL：空指针常量
EOF：表示文件结束的负整数
stdin，stdout，stderr：指向FILE类型的指针，分别对应标准输入，标准输出，标准错误
还有一些特点函数使用的宏
## 3.库函数
#### 3.1 文件访问
用于打开、关闭文件，刷新缓冲区
(1)`fopen()`和`fclose()`
`FILE *fopen(const char *filename, const char *mode)`
以mode的模式打开filename指向的文件
返回值：返回一个 FILE 指针，否则返回 NULL，且设置全局变量 errno 来标识错误
mode

| r | 只读，文件必须存在 | r+ | 可读可写，文件存在 |
| --- | --- | --- | --- |
| w | 只写。如果文件存在，则清除文件内容，否则创建一个新文件 | w+ | 创建一个用于读取的文件 |
| a | 从文本末尾开始写入内容 | a+ | 打开一个用于读取和追加的文件 |

`int fclose(FILE *stream);`
关闭流stream，刷新缓冲区
返回值：关闭成功返回0，失败返回EOF
(2)`int fflush(FILE *stream)`
刷新输出缓冲区，如果打开文件，则把输出缓冲区的内容写入该文件，否则清除缓冲区
返回值：成功，该函数返回0。发生错误，则返回 EOF，且设置错误标识符（ferror）
#### 3.2 输入输出函数
**1.非格式化输入输出**
(1)`fgetc()`和`getc()`
从流stream中读取下一个字符，并且将位置标识符后移一位
两者的区别在于`getc()`可以作为宏被调用，所有其参数不能带有副作用（例如fp++）
返回读取的字符
(2)`fputc()`和`putc()`
把字符发送到流stream中，并且将位置标识符后移一位
两者区别与上述相同，`putc()`也可作为宏
返回输入的字符
(3)`fgets()`和`fputs()`
声明：`char *fgets(char *str, int n, FILE *stream)`
从流stream中读入一行，并保存到`str`指向的字符串。当读到n-1个字符后，或读到换行符或到文末时结束
声明：`int fputs(const char *str, FILE *stream)`
把字符串写入到指定的流 stream 中，但不包括空字符
(4)`ungets()`
把字符 char（一个无符号字符）推入到指定的流 stream 中，以便它是下一个被读取到的字符。例如：
```c
 while(!feof(fp))  
   {  
      c = getc (fp);  
      /* 把 ! 替换为 + */  
      if( c == '!' )  
      {  
         ungetc ('+', fp);  
      }  
```
返回推入的字符
**2.二进制输入输出**
`fread()`和`fwrite()`
声明：`size_t fread(void *ptr, size_t size, size_t nmemb, FILE *stream)`
从流stream中读取数据并储存到ptr指向的数组中
声明：`size_t fwrite(void *ptr, size_t size, size_t nmemb, FILE *stream)`
将ptr指向数组的数据写入流stream
示例：
```c
#include <stdio.h>
#include <string.h>
 
int main()
{
   FILE *fp;
   char c[] = "This is runoob";
   char buffer[20];
 
   /* 打开文件用于读写 */
   fp = fopen("file.txt", "w+");
 
   /* 写入数据到文件 */
   fwrite(c, strlen(c) + 1, 1, fp);
 
   /* 查找文件的开头 */
   fseek(fp, 0, SEEK_SET);
 
   /* 读取并显示数据 */
   fread(buffer, strlen(c)+1, 1, fp);
   printf("%s\n", buffer);
   fclose(fp);
   
   return(0);
}
```
`fread()`和`fwrite()`可以直接处理二进制文件(.bin)
**3.格式化输入输出**
(1)`scanf()`，`fscanf()`和`sscanf()`
`scanf()`：从标准输入stdin读取格式化输入
`fscanf()`：从流stream中读取格式化输入，例如：
```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
   char str1[10], str2[10], str3[10];
   int year;
   FILE * fp;

   fp = fopen ("file.txt", "w+");
   fputs("We are in 2014", fp);
   
   rewind(fp);//将位置指针指向文件开头
   fscanf(fp, "%s %s %s %d", str1, str2, str3, &year);
   
   fclose(fp);
   
   return(0);
}
```
`sscanf()`：从字符串读取格式化输入，例如：
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main()
{
   int day, year;
   char weekday[20], month[20], dtm[100];

   strcpy( dtm, "Saturday March 25 1989" );
   sscanf( dtm, "%s %s %d  %d", weekday, month, &day, &year );
 
   return(0);
}
```
返回值：返回成功匹配或赋值的个数
(2)`printf()`，`fprintf()`和`sprintf()`
`printf()`：将格式化输出发送到标准输出stdout
`fprintf()`：将格式化输出发送到流stream，例如：
```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
   FILE * fp;

   fp = fopen ("file.txt", "w+");
   fprintf(fp, "%s %s %s %d", "We", "are", "in", 2014);
   
   fclose(fp);
   
   return(0);
}
```
`sprintf()`：将格式化输出发送到字符串，例如：
```c
#include <stdio.h>
#include <math.h>

int main()
{
   char str[80];

   sprintf(str, "Pi 的值 = %f", M_PI);
   puts(str);
   
   return(0);
}
```
返回值：成功，返回写入的字符总数
(3)`perror`
声明：`void perror(const char *str)`
字符串发送到标准错误stderr，首先输出字符串 **str**，后跟一个冒号，然后是一个空格
示例：
```c
#include <stdio.h>

int main ()
{
   FILE *fp;

   /* 首先重命名文件 */
   rename("file.txt", "newfile.txt");

   /* 现在让我们尝试打开相同的文件 */
   fp = fopen("file.txt", "r");
   if( fp == NULL ) {
      perror("Error: ");
      return(-1);
   }
   fclose(fp);
      
   return(0);
}
```
输出结果：Error: : No such file or directory


#### 3.3 文件定位
(1)`fseek()`
声明：`int fseek(FILE *stream, long int offset, int whence)`
设置流stream的文件位置为给定的偏移offset，参数offset意味着从给定的whence位置查找的字节数

|whence|含义|
|---|----|
|SEEK_SET|文件开头|
|SEEK_CUT|文件当前位置|
|SEEK_END|文件的末尾|

示例：
```c
#include <stdio.h>

int main ()
{
   FILE *fp;

   fp = fopen("file.txt","w+");
   fputs("This is obsidian", fp);
  
   fseek( fp, 7, SEEK_SET );//将位置标识符移到开头后的第7个字符
   fputs(" C Programming Langauge", fp);
   fclose(fp);
   
   return(0);
}
```
输出结果This is C programming Language
成功，返回0
(2)`ftell()`
声明：`long int ftell(FILE *stream)`
返回文件当前位置
(3)`rewind()`
将文件位置标识符置于开头
(4)`fgetpos()`和`fsetpos()`
声明：`int fgetpos(FILE *stream, fpos_t *pos)`
将文件的位置储存到pos中
声明：`int fsetpos(FILE *stream, const fpos_t *pos)`
将文件的位置设置到pos处
示例：
```c
#include <stdio.h>

int main ()
{
   FILE *fp;
   fpos_t position;

   fp = fopen("file.txt","w+");
   fgetpos(fp, &position);
   fputs("Hello, World!", fp);
  
   fsetpos(fp, &position);
   fputs("这将覆盖之前的内容", fp);
   fclose(fp);
   
   return(0);
}
```
成功，返回0
(5)`feof()`
声明：``int feof(FILE *stream)
测定文件的结束标识符
#### 3.4 文件操作
(1)缓冲`setbuf()`和`setvbuf()`
声明：`void setbuf(FILE *stream, char *buffer)`
定义流 stream 应如何缓冲。该函数应在与流 stream 相关的文件被打开时，且还未发生任何输入或输出操作之前被调用一次
示例：
```c
#include <stdio.h>

int main()
{
   char buf[BUFSIZ];

   setbuf(stdout, buf);
   puts("This is obsidian");

   fflush(stdout);
   return(0);
}
```
声明：`int setvbuf(FILE *stream, char *buffer, int mode, size_t size)`
定义流 stream 应如何缓冲
mode：定义流stream缓冲的模式

|mode| 含义  |
|---|---|
|\_IOFBF|**全缓冲**：对于输出，数据在缓冲填满时被一次性写入。对于输入，缓冲会在请求输入且缓冲为空时被填充。|
|\_IOLBF|**行缓冲**：对于输出，数据在遇到换行符或者在缓冲填满时被写入，具体视情况而定。对于输入，缓冲会在请求输入且缓冲为空时被填充，直到遇到下一个换行符。|
|\_IONBF|**无缓冲**：不使用缓冲。每个 I/O 操作都被即时写入。buffer 和 size 参数被忽略。|

(2)`remove()`和`rename()`
声明：`int remove(const char *filename)`
删除文件名，使其不能再被访问
声明：`int rename(const char *old_filename, const char *new_filename)`
将旧文件名更换为新文件名
(3)`tmpfile()`
声明：`FILE *tmpfile(void)`
以二进制更新模式(wb+)创建临时文件。被创建的临时文件会在流关闭的时候或者在程序终止的时候自动删除