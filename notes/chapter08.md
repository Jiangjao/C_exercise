# 第八章课后习题

## 一、问答题
### 1、在下面的代码中，*ptr和*（ptr+2)的值分别是多少？

1) int *ptr;
    int torf[2][2] = { 12, 14, 16};
    ptr = torf[0];
#### 分析
ptr这时候是列指针；
torf[2][2] = {{12, 14},{16}};
*ptr 指向了torf的第一列第一个元素的地址；
由于C语言这块数组内存是连续线性排列的，*(ptr + 2) -> *(torf[0] + 2)指向下一列第一个元素的地址；

12;16
------------------
2) int *ptr;
    int torf[2][2] = {{12},{14,16}};
    ptr = torf[0];
#### 分析
ptr这时候是列指针；
torf[2][2] = {{12},{14, 16}};
*ptr 指向了torf的第一列第一个元素的地址；
由于C语言这块数组内存是连续线性排列的，*(ptr + 2) -> *(torf[0] + 2)指向下一列第一个元素的地址；

12;14

### 2、在下面的代码中，**ptr和 **(ptr + 1)的值分别是多少？
1)  int (*ptr)[2];
    int torf[2][2] = {12, 14, 16};
    ptr = torf;
#### 分析
ptr这时候是行指针；
torf[2][2] = {{12, 14},{16}};
*ptr 指向了torf的第一行第一个元素的地址；
*(ptr + 1)指向下一行第一个元素的地址；
12;16
2)  int (*ptr)[2];
    int torf[2][2] = {{12}, {14,16}};
    ptr = torf;
#### 分析
ptr这时候是行指针；
torf[2][2] = {{12, 0},{14,16}}; //一般默认值大概是0；
*ptr 指向了torf的第一行第一个元素的地址；
*(ptr + 1)指向下一行第一个元素的地址；
12;14

### 3、psa是一个内含20个元素的数组，每个元素都是指向int类型的指针。请写成psa的语句。
注意**数组指针**与**数组指针**的区别。

int *psa[20];
int [20] psa; 这样应该也能行。

## 二、问答题
### 1、说明如下给出的程序将打印出什么内容？
#include <stdio.h>

int main()
{
    int ref[] = {8, 4, 0 ,2};
    int * ptr;
    int index;
    for(index = 0, ptr = ref; index < 4; index++, ptr ++){
        printf("%d %d\n", ref[index], *ptr);
    }
    return 0;
}
#### 分析：
ptr是指向数组ref的指针,数组ref[index]取值；*ptr取左值；
取的值位于同一块内存中。
8 8
4 4
0 0
2 2








