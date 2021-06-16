# 第3章课后题目

## 一. 问答题

### 1、如何使用printf()输出short、int、long类型的整数，请举例说明。
#include <stdio.h>


int main(){
    int interget = 1;
    short int i = 13;
    long int j = 123456001;
    puts("I said C language is very good");
    printf("short=%hd, int=%d, long=%ld\n",i, interget, j);
    //无符号类型.
    printf("short=%hu, int=%u, long=%lu\n",i, interget, j);
    return 0;
}

### 2、如何用printf输出float、double类型的整数，请举例说明。
#include <stdio.h>

int main(){
    float a = 1.1;
    double b = 13.123;
    puts("I said C language is very good");
    printf("float=%f, double=%lf\n", a,  b);
    return 0;
}

### 3、如何用printf()输出八进制、十进制和十六进制的数据，请举例说明。
#include <stdio.h>


int main(){
    // 八进制
    int a = 015;
    // 十六进制
    int b = 0X2A;
    // 十进制
    int c = 10;
    puts("I said C language is very good");
    // 以八进制输出
    printf("bajinhzhi=%o, shijingzhi=%o,shiliujinzhi=%o\n", a,  b, c);
    // 以十进制输出
    printf("bajinhzhi=%d, shijingzhi=%d,shiliujinzhi=%d\n", a,  b, c);
    // 以十六进制输出
    printf("bajinhzhi=%x, shijingzhi=%x,shiliujinzhi=%x\n", a,  b, c);
    return 0;
}





### 4、int类型的长度到底是多少？

C语言并没有严格规定short、int、long长度
-   short 至少2字节
-   int建议为一个机器字长，16位环境下，short和int为2字节，32位环境下字长4字节，64位环境下机器字节长度8字节
-   short长度不能大于int,long的长度不能小于int;
这也就是说长度（字节关系）：
2 ≤ short ≤ int ≤ long

### 5、定义两个float类型的变量f1和f2，如下所示:
float f1 = 3.3;
float f2 = 3.8;
它们转换成int类型后的值分别是多少？

<!-- core code: -->
float f1 = 3.3;
float f2 = 3.8;
int a,b;
a = (int)(f1);
b = (int)(f2);
printf("%d,%d\n",a,b);

然后控制台输出3,3；只保留了整数部分。

### 6、下面数学运算的结果是多少？
int a = 10 + 8 - 4 * 3 + 24 / 4 * 6 + 3;
结果是:45
1.加减法运算符优先级小于乘除法的,它们都是从左到右的。
2.表达式计算整体是从左到右的。

### 7、下面那几个是C语言的关键字？
int main function char =
-------------------------------
keywords是C语言规定的具有特定意义的字符串。
int main char


## 二. 编程题
### 1、一年大概有3.156 × 7 ^ 10秒，要求输入你的年龄，然后显示该年龄合多少秒。

#include <stdio.h>


int main(){
    long int age;
    long int seconds;
    long int c = 3.156e7;
    age = 24;
    seconds = age * c;
    printf("%e\n",seconds);
    printf("%d\n",seconds);
    return 0;
}

### 2、输入一个ASCII码值，输出它后面的字符。
#include <stdio.h>
int main(){
    char a,b;
    printf("input character a, b\n");
    scanf("%c %c",&a,&b);
    printf("%c %c\n",a+1,b+1);
    return 0;
}


## 三. 找错题
### 下面的代码有错吗？如果有，有几个，分别是什么错误？
#include
<stdio.h>
main(){
float r,pi=3.14;
scanf("%f\n",&r);
area = pi * r * r;
printf("area=%.2f\n",area);
}
这段代码的错误分别是：

<!-- 我觉得有问题的地方我注释了一番，还请指教 -->
#include <stdio.h> // 说不出来的语法格式
int main(){      // 正确主程序入口
    float r,pi=3.14;
    float area;   // 没有声明area
    printf("please enter the radius of circle \n" );  // 这一句可以去除，只是为了提示
    scanf("%f",&r);   // 换行符操作过于复杂
    area = pi * r * r;
    printf("area=%.2f\n",area);
    return 0;        // 主函数返回值
}

tips:
1. 在计算机内存中，整数一律采用补码的形式来存储。这意味着，当读取整数时还要采用逆向的转换，也就是将补码转换为原码。 
2. 小数位置和整数位置存储方式不同，但是都得转换成01，机器识别
3. %hd和%d表示以有符号的形式输出，所以还要经过一个逆向的转换过程：
4. %#x表示以无符号的形式输出，而无符号数的补码和原码相同，所以不用转换了，直接输出 0xffffffff 即可。
5. 注意，[1000 0000 …… 0000 0000]补是一个特殊的补码，无法按照本节讲到的方法转换为原码，所以计算机直接规定这个补码对应的值就是 -231， 

<!-- 4 和啥子要看？？C语言整数的取值范围以及数值溢出
7.小数在内存中是如何存储的
看到了chapter No.9 -->
