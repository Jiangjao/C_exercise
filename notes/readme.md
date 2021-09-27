## 普通warning
### 中文乱码改变方式
chcp 65001

### const pointer && point to const

const char*, char const*, char*const的区别问题几乎是C++面试中每次都会有的题目。

事实上这个概念谁都有只是三种声明方式非常相似很容易记混。
Bjarne在他的The C++ Programming Language里面给出过一个助记的方法：
把一个声明从右向左读。

char  * const cp; ( * 读成 pointer to )
cp is a const pointer to char

const char * p;
p is a pointer to const char;

char const * p;
同上因为C++里面没有const*的运算符，所以const只能属于前面的类型。

### EOF
EOF 本来表示文件末尾，意味着读取结束，但是很多函数读取错误时也返回EOF，
那么当返回EOF时，到底是文件读取完毕了还是读取错误了？可以借助stdio.h中的两个函数判断。

### 字符与字符数组
字符的索引值是个偏移量，计算机在存储器中以`连续字节`的形式保存字符，并用索引计算字符在存储器中的位置。
那么，就是说，当时设计的时候，计算机并不清楚字符串的长度。

那么，结尾处就得加上一个NUL ，在ASCII码中叫做 \0(哨兵),来表明其结尾。
- 双引号定义的字符串又叫做字符串字面量(string literal)
- 字符串字面量是常量；
- 所处位置也不同？

### 联合
```c
#include <stdio.h>
typedef union{
    short count;
    float weight;
    float volume;
}  quantity;
// C89表示法只能设置第一个字段
int main(){
    // C89方式
    quantity q = {4};
    // 指定初始化器(designated initializer),这个也可以设计struct的值
    quantity q = {.weight=1.5};
    // 点表示法
    quantity q;
    q.volume = 3.7;
    return 0;
}

```
无论用哪种方法设置联合的值，都会保存一条数据。联合只是提供了方法。

### C语言的堆
C语言非常古老，发明它的时候，绝大多数语言都没有自动“垃圾回收”装置
-   使用strup()函数会调用malloc()函数吗？
    -   这个取决于C标准库是如何实现的，通常情况下，是这样的。
操作系统会在程序(进程)结束时清除所有存储器。

### C的指针
函数名可以引用某段代码,引用存储器中的某样东西.
在C语言中,函数名也是指针变量

-   指针的声明有多种方式
    -   但是C语言没有函数类型,因为函数的类型不止一种.
    -   eg. int functionname(type arguments)
    -   调用:
        -   返回类型 (* 指针变量 )( 参数类型 )
由此可以推知函数指针的表示方法更复杂
-   由于是函数指针,调用函数时可以加*
    -   即调用时,match(ADS[i])换成(*match(ADS[i]))也行.

函数指针数组,一种更复杂的表示方式:
-   replies[] = {dump, second_chance, marriage};
    -   void (*replies[])(response) = {dump, second_chance, marriage};

### 标准头文件目录
通常类UNIX操作系统(如Mac或Linux)中，编译器会在以下目录查找头文件：
/usr/local/include
/usr/include

如果是MinGW的gcc,编译器会在下面这个目录中查找:
C:\MinGW\include

#### 共享.h头文件
1.  将头文件复制到/usr/local/include这样的标准目录中，就可以在源代码中用尖括号使用
    -   #include <encrypt.h>
2.  在include语句中使用完整语句路径名。
    -   #include "/my_header_files/encrypt.h"
3.  告诉编译器去哪里找头文件。
    -   可以使用gcc的-I选项
    -   gcc -I/my_header_files test_code ... -o test_code

### 动态库
绝大部分操作系统都支持动态库
gcc -shared hfcal.o -o

-shared选项告诉gcc你想把.o目标文件转化为动态库。编译
器创建动态库时会把库的名字保存在文件中，假设你在Linux
中创建了一个叫libhfcal.so的库，那么libhfcal.so文件就会记住它的库名叫hfcal。也就是说，一旦你用某个名字编译了库，就不能再修改文件名了，这一点很重要。
若想重命名库，就必须用新的名字重新编译一次。
- windows的MinGW
  - C:\libs\hfcal.dll
-   windows的Cygwin
    -  /libs/libhfcal.dll.a
-    Linux或Unix
    -  /libs/libhfcal.so
-  Mac
   -  /libs/libhfcal.dylib

#### Linux动态库的使用
但Linux就不一样了。
在Linux和大部分Unix中，编译器只会记录libhfcal.so库的文件名，
而不会包含路径名。也就是说如果不把hfcal库保存到标准目录（如
/usr/lib），程序就找不到它。为了解决这个问题，Linux会检查保
存在LD_LIBR ARY_PATH变量中的附加目录。只要把库目录添加
到LD_LIBRARY_PATH中，并export①它，elliptical就能找到
libhfcal.so

是不是有点复杂？是的，这就是为什么绝大部分使用动态库的程序
要把动态库保存在标准目录下。在Linux和Mac中，动态库通常保存
在/usr/lib或/usr/local/lib中；而在Windows中，程序员通常把.DLL和
可执行文件保存在同一个目录下。

