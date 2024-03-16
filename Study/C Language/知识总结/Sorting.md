#### 1.冒泡排序
遍历所有相邻的元素，如果它们顺序不对就将它们调换过来，直到顺序正确。
示例：
```c
#include <stdio.h>
void bubble_sort(int arr[], int len) {
    int i, j, temp;
    for (i = 0; i < len - 1; i++)
        for (j = 0; j < len - 1 - i; j++)
            if (arr[j] > arr[j + 1]) {
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }//相当swap函数
}
int main() {
    int arr[] = { 22, 34, 3, 32, 82, 55, 89, 50, 37, 5, 64, 35, 9, 70 };
    int len = (int) sizeof(arr) / sizeof(*arr);
    bubble_sort(arr, len);
    int i;
    for (i = 0; i < len; i++)
        printf("%d ", arr[i]);
    return 0;
}
```
注：
1. 冒泡排序首先将最大的数排到正确的位置上
2. 冒泡排序具有稳定性
#### 2.选择排序
在所有数据中找到最小值（或最大值），放到数据的第一位（与第一个数据交换位置）。再从剩下未排序的数据中找到最小值（或最大值），放到未排序数据的首位。重复操作，直到顺序全部排好。
示例：
```c
void selection_sort(int a[], int len) 
{
    int i,j,temp;
 
    for (i = 0 ; i < len - 1 ; i++) 
    {
        int min = i;                  // 记录最小值，第一个元素默认最小
        for (j = i + 1; j < len; j++)     // 访问未排序的元素
        {
            if (a[j] < a[min])    // 找到目前最小值
            {
                min = j;    // 记录最小值
            }
        }
        if(min != i)
        {
            temp=a[min];  // 交换两个变量
            a[min]=a[i];
            a[i]=temp;
        }
        /* swap(&a[min], &a[i]);  */   // 使用自定义函数交換
    }
}
 
/*
void swap(int *a,int *b) // 交换两个变量
{
    int temp = *a;
    *a = *b;
    *b = temp;
}
*/
```
#### 3.插入排序
通过构建有序序列，对于未排序数据，在已排序序列中从后向前扫描，找到相应位置并插入。从后向前扫描过程中，需要反复把已排序元素逐步向后挪位，为最新元素提供插入空间。
示例：
```c
void insertion_sort(int arr[], int len){
    int i,j,temp;
    for (i=1;i<len;i++){
            temp = arr[i];
            for (j=i;j>0 && arr[j-1]>temp;j--)
                    arr[j] = arr[j-1];
            arr[j] = temp;
    }
}
```
将未排序数的第一个与前面的有序数列比较，逐步前挪，直到插入自己正确的位置
#### 4.希尔排序
插入排序对于较有序数列排序效率高，但对于非常混乱的数列排序较慢
希尔排序：将整个数列分成几个子列进行排序，当整个数列基本有序时再按插入排序进行排列
示例：
```c
void shell_sort(int arr[], int len) {
    int gap, i, j;
    int temp;
    for (gap = len >> 1; gap > 0; gap = gap >> 1)
        for (i = gap; i < len; i++) {
            temp = arr[i];
            for (j = i - gap; j >= 0 && arr[j] > temp; j -= gap)
                arr[j + gap] = arr[j];
            arr[j + gap] = temp;
        }
}
```
#### 5.字典序
对字符串进行字典序的排序关键在于对<string.h>库函数的调用
在了解strcmp函数后，我们可以通过自定义的字典序来对字符串进行排序
```c
#include <stdio.h>
#include <string.h>

#define MAX_STRINGS 100
#define MAX_LENGTH 100
//定义排序函数，注意函数第一个参数是pointer to array
void sort_strings(char str[MAX_STRINGS][MAX_LENGTH], int n) {
    int i, j;
    char temp[MAX_LENGTH];
	//冒泡排序法对字符串排序
    for(i = 0; i < n-1 ; i++) {
        for(j = i+1; j < n; j++) {
            if(strcmp(str[i], str[j]) > 0) {
                strcpy(temp, str[i]);
                strcpy(str[i], str[j]);
                strcpy(str[j], temp);
            }
        }
    }
}

int main() {
    char str[MAX_STRINGS][MAX_LENGTH];
    int n, i;

    printf("请输入字符串的数量：");
    scanf("%d", &n);

    printf("请输入字符串：\n");
    for(i = 0; i < n; i++) {
        scanf("%s", str[i]);
    }

    sort_strings(str, n);

    printf("按字典序排序后的字符串：\n");
    for(i = 0; i < n; i++) {
        printf("%s\n", str[i]);
    }

    return 0;
}
```