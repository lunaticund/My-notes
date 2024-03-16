### 数列计算
**遍历数列**
`for`循环
计算$\pi$

判断素数
for循环也可以带else，没有break就执行else

蒙特卡洛算法：随机数
估计$\pi$
产生随机数
```python
import random
x=ramdom.random()*2-1
y=random.random()*2-1
#x=random.uniform(-1,1)
```
random()产生\[0,1)均匀分布
randint(a,b)\[a,b)之间的随机数
seed()用一个种子，使得每一次运行程序时都返回固定的随机数

迭代法：用旧值得到新值
Euclid算法，Fibonacci数列
方程数值求解，非线性方程：逐次逼近

Newton's method：在方程的单根附近平方收敛
找到函数$f(x)$在初始值$x_0$处的切线，切线与$x$轴的交点作为下一次$x$的值，不断迭代
