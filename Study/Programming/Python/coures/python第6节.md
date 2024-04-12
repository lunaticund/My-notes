Bisection Method求解非线性方程组（二分法$\log_2N$）
只能在一个区间找到一个解
eval() 
print(\*list)：参数解包，打印元素，空格分隔

```
n="312312"
lst1=list(n)
lst2=list(map(int,lst1))
```
list()函数
列表中的表达式是会计算的。

列表元素可以直接赋值
```python
#s1,s2都是列表
s1=s2#s1,s2指向同一个列表
s1=s2.copy()#赋值一个列表副本
```
也可用切片来创建副本，切片也可以放在=左边
```python
lst[2:3]=[]#让一段切片变为[]
lst[2]=[]#让一个元素变为[]
#两者结果不一样
```

删除元素
del语句
`del list[3]`

读入实验数据
一行数据，直接list(map(int,input().split()))

一行是数据带表达式：eval(input())
eval()会计算表达式，产生结果
三种情况：1.数据带十六进制或八进制字面量 2.带有四则运算 3.数据式列表或元组的格式

多行数据：
每行一个数据，直接一个循环
每行多个数据：每行新增的数据用extend()连接到原来的列表末尾

join()：用字符串做分隔符将列表中的元素组成一个字符串
```python
a=['hello','good','boy']
print(' '.join(a))
print(':'.join(a))
```
判断空表：
```python
t=[]
print(t==[])
print(len(t)==0)
print(not t)#性能最好
```
抛空列表
```python
line = input().split()
while line:
		print(line.pop(0))
```


判断素数，只需判断它是否能被它之前的素数整除
每判断一个素数就把他加入素数表中
另一种思路，先构造一个表，从2开始，**删除所有2的倍数**，再删除所有3的倍数···，直到只剩下素数

秦九韶算法：计算多项式