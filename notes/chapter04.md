# 第4章课后题目

## 一、编程题
### 1、你需要写一个程序，读入当前的相对空气湿度H（0.0≤H≤100.0）,气象学家小葱头认为当相对湿度大于55.4时，就属于“很可能会下雨”的天气。请根据今天的相对湿度，判断今天是否“很可能会下雨”的天气。

要求：输入一个实数（0-100）,表示相对湿度H，输出为一行，如果H>55.4,则输出YES,表示会下雨；否则会输出NO,表示不会下雨。
#include <stdio.h>

int main()
{
    float humidity;
    printf("please input the humudity of today\n");
    scanf("%f", &humidity);
    
    if ((humidity > 0.0) && (humidity < 100)){
        if (humidity >= 55.4)
            printf("YES,it seems very possible to rain today");
        else
            printf("NO,emm, hard to say  raining today");
    }else{
        printf("the humidity is seems not correct,please input the humidity between 0 to 100");
        }
    return 0;
}

### 2、任意输入3个整数，编程实现对这3个整数由小到大进行排序。
#include <stdio.h>
// #include <stdlib.h>

int main()
{
    int a,b,c,t;
    scanf("%d %d %d",&a, &b, &c);
    if(a > b) { t=a; a=b; b=t;}
    if(a > c) { t=a; a=c; c=t;}
    if(b > c) { t=b; b=c; c=t;}
    printf("%d %d %d\n",a ,b, c);
    return 0;
}

### 3、编写程序输出九九乘法表，如下所示：
1*1 = 1 1*2 = 2 1*3 = 3 1*4 = 4 1*5 = 5 1*6 = 6 1*7 = 7 1*8 = 8 1*9 = 9
2*1 = 2 2*2 = 4 2*3 = 6 2*4 = 8 2*5 =10 2*6 =12 2*7 =14 2*8 =16 2*9 =18
3*1 = 3 3*2 = 6 3*3 = 9 3*4 =12 3*5 =15 3*6 =18 3*7 =21 3*8 =24 3*9 =27
4*1 = 4 4*2 = 8 4*3 =12 4*4 =16 4*5 =20 4*6 =24 4*7 =28 4*8 =32 4*9 =36
5*1 = 5 5*2 =10 5*3 =15 5*4 =20 5*5 =25 5*6 =30 5*7 =35 5*8 =40 5*9 =45
6*1 = 6 6*2 =12 6*3 =18 6*4 =24 6*5 =30 6*6 =36 6*7 =42 6*8 =48 6*9 =54
7*1 = 7 7*2 =14 7*3 =21 7*4 =28 7*5 =35 7*6 =42 7*7 =49 7*8 =56 7*9 =63
8*1 = 8 8*2 =16 8*3 =24 8*4 =32 8*5 =40 8*6 =48 8*7 =56 8*8 =64 8*9 =72
9*1 = 9 9*2 =18 9*3 =27 9*4 =36 9*5 =45 9*6 =54 9*7 =63 9*8 =72 9*9 =81

#include <stdio.h>
// #include <stdlib.h>

int main()
{
    for (int i = 1; i <=9;i++){
        
        for (int j = 1;j <= 9; j++){
            printf("%d*%d =%2d ",i,j,i*j);
        }
        printf("\n");
    }
    return 0;
}

### 4、修改第3题中的程序，使之输出如下格式的九九乘法表：
1*1 = 1 1*2 = 2 1*3 = 3 1*4 = 4 1*5 = 5 1*6 = 6 1*7 = 7 1*8 = 8 1*9 = 9 
2*2 = 4 2*3 = 6 2*4 = 8 2*5 =10 2*6 =12 2*7 =14 2*8 =16 2*9 =18
3*3 = 9 3*4 =12 3*5 =15 3*6 =18 3*7 =21 3*8 =24 3*9 =27
4*4 =16 4*5 =20 4*6 =24 4*7 =28 4*8 =32 4*9 =36
5*5 =25 5*6 =30 5*7 =35 5*8 =40 5*9 =45
6*6 =36 6*7 =42 6*8 =48 6*9 =54 
7*7 =49 7*8 =56 7*9 =63
8*8 =64 8*9 =72
9*9 =81

#include <stdio.h>
// #include <stdlib.h>

int main()
{
    int j;
    j = 1;
    for (int i = 1; i <=9;i++){
        
        for (;j <= 9; j++){
            printf("%d*%d =%2d ",i,j,i*j);
        }
        j = i + 1;
        printf("\n");
    }
    return 0;
}
