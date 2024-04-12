模块
```python
from <name> import <function>
import <name>
```
`improt`实际上是将模块内的代码全部执行。

```python
if __name__ == '__main__':
	print('hello')
```
作为程序直接被执行时，会输出hello

## 递归计算
通过函数调用自己进行的重复计算

例：阶乘计算
```python
def f(x):
	if x==1:
		return 1
	else:
		return x*f(x-1)
```
递进(分解)和回归
递进时不做计算
例：斐波那契数列
```python
def f(n):
	if n==0 or n==1:
		return n
	else:
		return f(n-1)+f(n-2)
```

阶乘为线性递归，斐波那契为树状递归

树状递归具有大量的重复计算
使用字典进行记忆
```python
def fib(n,fibm={0:0,1:1}):
	if n not in finbm:
		fibm[n]=fib(n-1)+fib(n-1)
	return fibm[n]
```

**尾递归：**
不对返回的值进行任何计算，回归不做计算
python会自动进行尾递归优化

**遍历嵌套列表：**
```python
def numb(lis):
	cnt=0
	for x in lis:
		if isinstance(x,list):
			cnt+=numb(x)
		else:
			cnt+=1
```

汉诺塔

快速幂：
