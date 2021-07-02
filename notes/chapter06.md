# 第6章课后题目

## 一、问答题
### 1、使用函数时，局部变量能否和全局变量重名？
可以。
### 2、一个函数中， return只能有一个吗？
可以有多个，如条件判断语句。

### 3、根据下面对各个函数的描述，分别编写它们的函数头。
1) donut()接受一个int类型的参数，直接输出指定参数个0；
void donut(int argument); 
2) gear()接受两个int类型的参数，返回int类型的值；
int gear(int a, int b);
3) guess()不接受任何参数，返回一个int参数的值；
int guess();
4) n_to_char()接受一个int类型的参数，返回一个char类型的值。
char n_to_char(int a);

## 二、编程题
### 1、设计一个函数，返回2个整数的和。
int add(int a, int b){  //a, b为局部变量
    return a + b;
}

### 2、编写一个函数，返回3个整数中的最大值。
int compare(int a, int b, int c){  
    int temp;
    temp = a>b?a:b;
    temp = c>temp?c:temp;
    return temp;
}
### 3、设计一个函数choices(ch,i,j)，打印指定的字符j行i列。
<!-- env:gcc version 6.3.0 (MinGW.org GCC-6.3.0-1)  vscode + windows 10 -->
void choices(char string[3][2], int i, int j){
    printf("%c",string[i][j]);
}

int main(){
    // int c = 8;
    int i, j;
    char string[3][2]={{'c', 'p'},{'r', 'o'},{'g', 'r'}};
    for(i=0; i<3; i++){
        for(j=0; j<2; j++){
            printf("%c",string[i][j]);
        }
    }
    // printf("%c",string[2][1]);
    printf("\n");
    dumpChar(string, 1,1 );
    // printf("the length is %d:", strlen(string));
    // printf("%d\n", compare(a ,b ,c));
    return 0;
}

### 4、编写程序，从键盘输入一个数，求出这个数的阶乘。
int factorial(int a){
    int i = 1;
    int index = 1;
    if(a ==1 || a==0){
        i = 1;
    }
    for(index; index <= a; index++){
        i *= index;
    }
    printf("%d",i);
    return i;
}
int main(){
    int i, j;
    scanf("%d", &i);
    factorial(i);
    return 0;
}
## 三、纠错题
### 判断下面的函数定义是否正确？如果不正确，指出错误。
void salami(num)
{
    int num, count;
    for(count = 1; count <= num; num++)
    {
        printf(" o salami mio!");
    }
}
----------------------------------------------------------
void salami(int num)   // 未指明类型，且少了参数
{
    int num, count;
    for(count = 1; count <= num; num++)  // 死循环
    {
        printf(" o salami mio!");
    }
}
