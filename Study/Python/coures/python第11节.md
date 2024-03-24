# 异常和文件

## 异常处理：
`try`：分离的业务逻辑和错误处理
```python
try:
	something
except:
	something
```
try后面的语句一条一条执行，有一条出错之后的语句都不执行
![[Pasted image 20240317221218.png]]
最后一个except捕捉所有错误
无异常，会执行else的语句
finally一定会执行

raise用于抛出异常
```python
raise Exception('fault')
```
![[Pasted image 20240317221713.png]]

一次捕捉多个异常
```python
except (TypeErroe,KeyError):
```

异常和函数
告诉你是如何一步一步出现异常的

异常变量
```python
except TyprError as name:
	print(name)
```
对于万能捕捉器
```python
except Exception as name:
```


断言
```python
assert <条件>, <失败提示词>
def divide(a,b):
	assert b!=0,"Divided by zero"
	retuen a/b
```
断言出错，返回失败提示词
断言用于防止他人调用过程时传递错误参数

## 文件
二进制和文本
打开文件，处理数据，关闭文件
`open()`
UTF-8每个汉字3个字节，英文字符1个字节
当前目录可以直接打开，其他目录使用路径打开

打开文件
```python
filetxt=open('File_name','modle')
```
modle：'r' , 'w' , 'a' , ''x , '+' , 't' , 'b'
![[Pasted image 20240317224656.png]]

文件迭代器
文件很大时，readlines()占用很大的内存
```python
f=open('name','r+')
for line in f:
	print(line)
```
一次给出一行文本

编码问题
```python
f=open('','',encoding='GBK')
```

重定向
```python
import sys
s=sys.stdin.readlines()
print(s)
```

文件与异常
```python
try:
	f=open('')
except:
	print('Fail')
finally:
	f.close()

```

```python
with open('1.txt') as file:
	data=file.read()
```
做所有的except和close