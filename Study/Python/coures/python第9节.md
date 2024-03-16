# 函数
## 定义函数：
### 函数
```python
def func(*coef):
	mainbody
```
python函数call-by-value
函数需要先定义（没有声明一说）
python解释器只记录函数而不解析。不被调用则不被执行

## 参数类型
**位置参数**
传入的参数的值按照顺序依次复制
```python
func(1,2,3,4)
```
**关键字参数**
```python
func(x1=1,x2=2,y1=4,y2=5)
```
两者可以混合用，当位置参数只能在前面
**默认值参数**
```python
def func(x1,x2,y1,y2=5)
#若调用时没有传入y2，则按默认值计算
```
在函数对象被创建时被创建
```python
def in(arg,lis=[])
	lis.append(arg)
	print(lis)
#每次进入函数时，lis不会被赋值为空列表，之前的数据仍在其中(持久存储)
```
**不定常参数**
```python
def count(a,*b):
	print(len(b))
```
多的变量被打包成一个Tuple
print函数
```python
print(*object,sep=" ",end="\n",file=sys.stdout)
```
```python
print(*lis)#实参解包
```
将参数收集到列表中(`**`)
```python
def count(a,**d):
	print(d)
count(3,X=1,y=2,z=3)
#结果：{'x':1,'y':2,'Z'=3}
```

仅限关键字参数
```python
def func(*,a,b):
	defualt
#必须以关键字参数传入
```

仅限位置参数
```python
def func(a,b,/,*args):
	print(a,b)
#前两个参数只能传位置参数
```

当实参是不可变对象时(number, string,tuple)，形参改变不会影响实参
当实参是可变对象时(list, set, dictionary)，形参改变会影响实参。类似指针
## 函数返回值
`return`用于返回值，无`return`返回None

python支持一次返回多个值
```python
def func(a,b):
	return a/b,a+b
x,y=func(1,2)
#实际返回值为一个元组
```
## 命名空间和作用域
变量第一次被创建时，它就处于那个命名空间。
局部，全局，内置。
每个函数内部都有自己的命名空间。

**局部变量和全局变量**
全局变量：定义在函数外，存在于整个程序。
局部变量：定义在函数内，存在于函数命名空间。

在函数内部，定义了局部变量，则先取局部的值，若未定义，则寻找全局变量。

希望使用全局变量，使用`global`关键字
```python
def scopa():
	gloable var
	var=1
```
全局变量也会被修改

如果已经创建局部变量，在使用global则出错
![[Pasted image 20240310091912.png]]

模块