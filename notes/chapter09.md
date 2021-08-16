# 第九章课后习题

## 一、编程题
### 1、 设计一个结构体模板，要求能够存储有关月份的如下信息：
-  1)月份的英文名称；
-  2)月份的英文简写；
-  3)月份号；
-  4)该月份的天数；
```c
#include <stdio.h>
#include <string.h>

int main(){
    struct monthProfile{
        char * fullname;
        char * verbosename;
        int numMonth;
        int daysContain;
    }ps = {"January", "Jan",1, 31};

    printf("%s",ps.verbosename);
    return 0;
}
```

### 2、分析如下程序代码：

```c
struct name
{
    char first[20];
    char list[20];
};
struct hem{
    int limbs;
    struct name title;
    char type[30];
};

struct hem *pb;

struct hem deb={
    6,
    {"Berbnazel","Gwolkapwolk"},
    "Arctruan"
};
pd = &deb;
```

请问，下面各个语句分别输出什么？
-   1)printf("%d\n", deb.limbs);
    -  output: 6

-   2)printf("%s\n", pb->type);
    -  output: Arctruan

-   3)printf("%s\n", pb->type + 2);
    -  output: ctruan 

分析：最后一个type类型是一串字符，那么实际当成字符数字处理即可。

### 3、编写程序，证明 int const * p1 和 int * const p2的区别。
```c
#include <stdio.h>
#include <string.h>

// 常量指针
int main(){
    // C++ Primer中黑体的两个术语是 
    // 1.指向常量的指针(pointer to const)和常量指针(const pointer)。

    // 2.这样记：const后边的内容为“常量”。
    const int a = 5;

    int x = 1;

    int const * p1 = &a;    // p1 是指针常量

    int *const p2 = &x;     // p2是指向x的常量指针

    printf("the value of *p1:%d\n",*p1);
    printf("the value of *p2:%d\n",*p2);

    // *p1 = 12;  // 由于 p1是指针常量，所以无法更改。
    *p2 = 12;
    return 0;
}
```
### 4、编写程序，随机输出10个90-100之间的数。
```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main(){
    int a,i;
    for (i = 0 ; i < 10; i++ ){
        srand((unsigned)time(NULL));
        a = rand() % 10 + 90;
        sleep(2); //延迟2s
        printf("%d\n",a);
    }
    return 0;
}
```

## 二、纠错题
### 1、下面创建的结构体模板正确吗？有哪些问题？
```c
struct {
    char itable;
    int num[20];
    char * togs;
}
// 更改完：
    struct test{
        char * itable;
        int num[20];
        char * togs;
    };
```