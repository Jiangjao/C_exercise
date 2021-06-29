# 第5章课后题目

## 一、问答题
### 1、内含10个元素的下标范围是什么？
0到9

### 2、正确声明以下各个变量:
1)digits是一个内含10个int类型的数组；
int digits[10];
2)rates是一个内含6个float类型的数组；
float rates[6];
3)mat 是一个内含3个元素的数组，而每个元素又是内含5个整数的数组；
int mat[3][5];
4)声明一个内含6个int类型的数组，并初始化个元素为1、2、4、8、16、32;
int test[] = {1, 2, 4, 8, 16, 32};

### 3、假设有下面的声明：
float rootbeer[10],things[10][5];
value=2.2;
判断以下各项是否有效
1)rootbeer[2] = value;   
无效，value 并未指明类型
----
2)things[5] = rootbeer;
无效，数组引用不正确
---
3)rootbeer = value;
无效，value 并未指明类型
---
4)thing[4][4] = rootbeer[3];
有效
---
## 二、编程题
### 1、编写程序，统计输入字符串（字符数不超过100）中的字符A的数量。

#include <stdio.h>
#include <string.h>

int main(){
    int num = 0,i;
    char b[100] = {};
    // 从控制台获取用户输入并赋值给数组元素
    gets(b);
    printf("sizeof b is %d",sizeof(b));
    for(i=0; i<100; i++){
        if(b[i] == 'A'){
            num += 1;
        }   
    }
    printf("The number of A is %d\n", num);
    return 0;
}

### 2、编写程序，实现将输入的字符串进行逆序输出。
#include <stdio.h>
#include <string.h>

int main(){
    int num = 0,i,j,length;
    printf("Please input the approximate length od string:\n");
    scanf("%d",&length);
    // 刷新缓冲区
    fflush(stdin);
    char b[length];
    printf("please input a string: \n");
    // 从控制台获取用户输入并赋值给数组元素
    gets(b);
    length = strlen(b);
    j = length;
    printf("sizeof b is %d\n",length);
    printf("The  reverse string is \n");
    for(i=0; i<length; i++){
        j -= 1;
        printf("%c",b[j]);
    }
    return 0;
}

### 3、利用数组解决线性代数中的矩阵转置问题，设有一矩阵为m X n 阶(即m行n列)，第i行j列元素是a(i,j),需要将该矩阵转置为n X m阶的矩阵，是其中元素满足b(i,j)=a(j,i)。

##### 分析
1.一般矩阵下标是数字，先从有限的矩阵数组测试；
#include <stdio.h>
// #include <stdlib.h>
#include <string.h>

int main()
{
    int i,j;
    int a[5][3];
    int b[3][5];
    printf("Input score:\n");
    for (i=0; i< 3; i++){
        for (j=0; j<5; j++){
            scanf("%d", &a[j][i]);
            b[i][j] = a[j][i];
            printf("the digit element of b is %d", b[i][j]);
        }
    }
    for (i=0; i< 3; i++){
        for (j=0; j<5; j++){
            printf("the digit element of b[%d][%d] is %d\n", i, j, b[i][j]);
            // sum += a[i][j];
        }
    }
    return 0;
}
2.用户输入特定的数组长度，基本可以满足一般数字数组的需求；
#include <stdio.h>
// #include <stdlib.h>
#include <string.h>

int main()
{
    int num = 0,i,j,x,y;
    printf("Please input the approximate dimesion(i, j) of matrix:\n");
    scanf("%d, %d",&i, &j);
    // 刷新缓冲区
    fflush(stdin);
    int a[i][j];
    int b[j][i];
    printf("Input score:\n");
    for (x=0; x< i; x++){
        for (y=0; y<j; y++){
            scanf("%d", &a[y][x]);
            b[x][y] = a[y][x];
            printf("the digit element of b is %d", b[x][y]);
        }
    }
    return 0;
}

3.至于矩阵存储混合类型的元素，字符、数字、二进制等，能力有限，暂不论述。