## 元组Tulpe
元组是一个与list相似的有序序列容器，使用`()`生成
可以被索引和切片
唯一区别，Tulpe不可修改，不能增加删除，也不能修改元素。
S
单个元素的元组
`(2,)`必须加上逗号，没有逗号时表示一个数
`tuple()`制造一个tuple

`enumerate()`：将一个可遍历的对象转换成一个索引序列
```python
seasons=['Spring','Summer','Fall','Winter']
print(list(enumerate(seasons)))
print(list(eunmerate(seasons,start=1)))
#输出结果
[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
[(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
#有四个元素列表，每个元素都是一个二元组
for i, element in enumerate(seasons):
	print(i,element)
```

## 集合set
集合是一个无序容器（内部储存有序，不能指定顺序），不能有相同元素，使用`{}`创建
创建一个空集合：`emp=set()`（不能直接用`{}`去创建集合）
`set()`也可将其他序列转成集合，自动删除重复元素
集合本身可变，但集合的元素是不可变的（无法通过下标访问）
增减元素：`add(),remove()`
操作函数：`len(),max(),min(),sum()`

操作访问集合元素：遍历
`for i in s`

元素，子集，超集和相等判断
`in`和`not in`用于判断元素是否再集合里面
使用`s1.issubset(s2)`判断s1是不是s2的子集
使用`s2.issuperset(s1)`判断s2是不是s1的超集
使用`==,!=`判断两个集合是否完全相等
关系运算符
`<,>`真子集，`<=,>=`子集

集合运算
并集：运算符`s1 | s2`，函数`s1.union(s2)`
交集：运算符`s1 & s2`，函数`intersection()`
差集：`s1-s2`结果是在s1中出现，在s2中不出现的元素集合，`s1-s2=s1-(s1&s2)`，函数`difference()`
对称差：`s1^s2`出去共同元素的所有元素，函数`symmertric_difference()`

集合的应用：
1. 数学运算中需要使用到集合运算
2. 利用集合的唯一元素性（hash算法，近似常数）

挑选名单
随机抽样：`random.simple()`

## 字典dictionary
字典是一个使用key来索引元素的集合，一个key与它对应的数据组成字典中的一个条目
使用`{}`表示，元素用`,`分隔，**使用`:`分隔key和value**
`student={3230101:'王二',3230102:'wenji'}`

空字典：使用`{}`或`dict()`创建
使用`{}`或`dict()`创建字典
![[Pasted image 20240302153355.png]]
`dict()`传入变量为列表时，元素必须是二元组，第一个作为index，更多的数据可以封装在一个元组里面
**key**
不可变对象可作为字典的key：数字，string，tuple
可变对象不能做key：list，dictionary

**访问和修改条目**
使用`[]`直接访问条目
`student[wenji]`
赋值
`score[wenji]=100`
增加元素
`score[tangji]=90`直接对需要增加的索引赋值
删除条目
`del score[wenji]`
遍历字典
```python
for name in score:#遍历key
	#内部需要使用name为索引访问条目
	pass
```
`len,in,not in,==,!=`
字典方法：
![[Pasted image 20240302154557.png]]
`keys(),values(),items()`返回的都是迭代器

`get()`和`[]`
如果找不到key，`get(key,value)`返回value（默认为None）,而`[]`KeyError
使用`[]`，最好在前面写`if key in score.keys()`
**字母，数字等计数都用字典去做**
`countchar[c]=countchar.get(c,0)+1`
r