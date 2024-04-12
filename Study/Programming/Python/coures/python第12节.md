列表字面量
列表`[]`里都是表达式，会进行计算

列表推导式
从一个或多个可枚举量创建列表
`[x**2 for x in range(10)]`

带条件的推到式
`[x**2 for x in range(10) if x%2==0]`
if 是一个筛选器

if 表达式
`1/x if x%2==1 else -1/x`

只是为了将代码简化

素数判断
```python
x=int(input())
not [i for i in range(2,x) if x%i==0]
```


多变量的列表推导式
两层for循环：
`[x*y for x in lis_x for y in lis_y]`
元素个数`len(lis_x)*len(lis_y)`

分别取出
`[x*y for x,y in zip(lis_x,lis_y)]`


**生成器**
列表，集合，字典都有推到式

对于元组
`c=(x for x in range(10))`
生成器可且仅可遍历一次（生成一次）

作为函数参数的生成器
`sum(x**x for x in range(10))`
`any()`如果生成器返回一个数，则返回True

**函数是基础类型**
函数可以被赋值给变量
函数可以传递给另一个函数
函数可以作为另一个函数的返回值

匿名函数
lambda表达式
将定义的简单函数赋值给一个变量

高阶函数
`map(f,sq)`将 f 函数作用于 sq 上。结果是一个可枚举量。
`list(map(lambda x y:x+y,[1,2,3,4,5],[5,6,7,8,9]))`

`filter(f,sq)`挑选出 sq 中对于函数 f 返回 True 的元素

`reduce()`