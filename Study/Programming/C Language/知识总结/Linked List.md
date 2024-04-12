## 1.链表和数组
**数组**：顺序储存
$\begin{cases}优点:可以直接找到想要去的位置\\缺点:不能动态分配内存，插入数据时需要移动大量数据\end{cases}$
**链表**：链式储存
$\begin{cases}优点:可以实现动态内存分配，插入或删除数据时只需修改改动出\\缺点:想达到某个位置，必须从头遍历之前的数据\end{cases}$
## 2.链表的实现
$\begin{cases}单链表\\双链表\\循环链表\end{cases}$
#### 1.单链表
单链表示意图：
![[单链表示意图.png]]
单链表由Head，Node，Tail组成
在Node中，DATA保存需要储存的数据，NEXT是指向下一个节点的指针
**Definition of Node**：
```c
struct Node{
	int num;
	double score;
	struct Node *next;//用于保存下一个节点的地址
}
```
**单链表的建立**：（头插入法）
```c
struct Node *head = NULL;
struct Node *temp;
//链表的初始化
temp = malloc(sizeof(struct Node));
temp->next = NULL;
head = temp;
//插入节点
for(int i=1;i<N;i++){
	temp = malloc(sizeof(struct Node));
	if(temp==NULL)
		printf("申请失败");
	/*对DATA的操作*/
	temp->next = head;
	head = temp;
}
```
尾插入法与此相似
#### 2.双链表
双链表示意图：
![[双链表示意图.png]]
为建立一个双链表，每个节点需要有两个指针，分别指向前一个节点和后一个节点。
头部的`pre`和尾部的`next`都指向`NULL`
**双链表的节点**：
```c
struct Node{
	int data;
	struct Node *pre;
	struct Node *next;
}
```
**双链表的建立**：
```c
struct Node *head = NULL;
struct Node *temp;
//初始化
temp = malloc(sizeof(struct Node));
temp->next = NULL,temp->pre = NULL;
head = temp;
//插入节点
for(int i=1;i<N;i++){
	temp = malloc(sizeof(struct Node));
	/*对data的操作*/
	head->pre = temp;
	temp->next = head;
	head = temp;
	temp->pre = NULL;
}
```
#### 3.循环链表
循环链表示意图：
![[循环链表示意图.jpg]]
循环链表在单链表的基础上只需要将最后一个节点的`next`指向第一个节点，当然也可以将双链表进行如此操作，实现双循环链表。
**循环链表的建立**：
```c
struct Node{
	int data;
	struct Node *next;
}//节点与单链表相同

struct Node *head = NULL。*tail;
struct Node *temp;
//链表的初始化
temp = malloc(sizeof(struct Node));
temp->next = NULL;
head = temp;
tail = temp;
//插入节点
for(int i=1;i<N;i++){
	temp = malloc(sizeof(struct Node));
	if(temp==NULL)
		printf("申请失败");
	/*对DATA的操作*/
	tail->next = temp;//与单链表相比，只是将尾部指头部
	temp->next = head;
	head = temp;
}
```
## 3.对链表的操作
$\begin{cases}遍历节点\\插入节点\\删除节点\end{cases}$
#### 1.遍历
**单链表**：输出前k个节点的数据，从`head`进入链表
```c
struct Node *temp = head;
for(int i=0;i<k;i++){
	printf("第%d个节点的值：%d",i+1,temp->data);
	temp = temp->next;	
}
```
对于双链表，可以正向遍历，也可以反向遍历
#### 2.插入节点
**单链表**：利用两个指针`p,t`，一前一后扫描链表。
某个节点后插入：`p`到达此节点后插入新节点
某个节点后插入：`t`到达时插入
![[单链表插入节点.jpg]]
节点前插入节点：
```c
struct Node *t,*p;
t = head
//判断目标节点是否是第一个
if(t->data = n){
	t = malloc(sizeof(struct Node));
	t->next = head;
	head = t;
	goto out;//调过循环
}
//扫描节点
do{
	p = t;
	t = t->next;
}while(t->data != n);
//判断节点是否是最后一个
if(t->next==NULL){
	t = malloc(sizeof(struct Node));
	t->next = NULL;
	p->next = t;
	goto out:
}
t = malloc(sizeof(struct Node));
t->next = p->next;
p->next = t;

out:
```
**双链表**：可正向扫描或逆向扫描
![[双链表插入节点.png]]
```c
do{
	p = t;
	t = t->next;
}while(t->data != n);
t = malloc(sizeof(struct Node));
//建立双向互指
t->next = p->next;
p->next->per = t;
p->next = t;
t->pre = p;
```
还需加入判断目标节点是否是第一个或最后一个的`if`
#### 3.删除节点
**单链表**：![[单链表删除节点.png]]
```c
struct Node *t,*p;
t = head
//判断目标节点是否是第一个
if(t->data = n){
	head = t->next;
	free(t);
	goto out;
}
//扫描节点
do{
	p = t;
	t = t->next;
}while(t->data != n);
//判断目标节点是否是最后一个
if(t->next==NULL){
	p->next = NULL;
	free(t);
	goto out;
}
p->next = t->next;
free(t);

out:
```
**双链表**：![[双链表删除节点.jpg]]
```c
struct Node *t,*p;
t = head
//判断目标节点是否是第一个
if(t->data = n){
	head = t->next;
	head->pre = NULL
	free(t);
	goto out;
}
//扫描节点
do{
	p = t;
	t = t->next;
}while(t->data != n);
//判断节点是否是最后一个
if(t->next==NULL){
	p->next = NULL;
	free(t);
	goto out;
}
p->next = t->next;
t->next->pre = p;
free(t);

out:
```
**插入节点和删除节点代码差别只在`malloc`变为`free`**
