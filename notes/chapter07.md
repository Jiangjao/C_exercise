# 第七章课后习题
## 一、问答题
### 1、有一段程序，如下所示
#define MA(x) x*(x-1)
int a=1,b=2;

请计算MA(1+a+b)的值，并编写程序进行验证。

#define MA(x) x*(x-1)
int a=1,b=2;

int main(){
    printf("%d", MA(1+a+b));
    return 0;
}
结果是:8
推测，是符号替换， 1+1*(1+a-1)+a + 1+1*(1+b-1)+b

### 2、读下面一段程序：
#define SUB(X,Y) (X)*Y
int a=3, b=4;
计算SUB(a++, b++)的值，并编写程序进行验证。

#define SUB(X,Y) (X)*Y
int a=3, b=4;
int main(){
    // printf("%d", MA(1+a+b));
    printf("%d", SUB(a++,b++));
    return 0;
}

结果是:12 
分析:宏只做替换；并非编译时的处理

### 3、设int b = 8;则正则表达式(b>>2)/(b>>1)的值是多少？
2/4 ,应该是0.5 ;但是我输出0.0000

### 4、若定义：
unsigned int a=3,b=10;
printf("%d\n",a<<2|b==1);
a<<2是 12 
b==1 是0
12 | 0 == 12  
| 代表了按位或
输出结果是多少？
12

## 二、编程题
### 1、设计一个带参数的宏，用来求2个整数的余数，并编写程序实现手动输出2个整数，通过宏调用输出最终结果。

#include <stdio.h>
#define modTest(x,y) ((x)%(y))
int main(){
    int a,b;
    scanf("%d", &a);
    scanf("%d", &b);
    printf("mode test %d", modTest(a,b));
    return 0;
}


### 2、编写程序，用带参数的宏，实现从3个数中找出最大的数。

#include <stdio.h>
#define judge(x, y) x>y?x:y
int main(){
    int a = 2;
    int b = 10; 
    int c = 1;
    printf("The biggest number is that:%d",judge((a,b),c));
    return 0;
}

