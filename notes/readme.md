<!--
 * @Author: xiao jiao
 * @Date: 2021-08-09 11:29:36
 * @LastEditTime: 2021-09-18 19:07:03
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \geekbang\C_exercise\notes\readme.md
-->
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
    typedef union{
        short count;
        float weight;
        float volume;
    }  quantity;
    // C89表示法只能设置第一个字段
    quantity q = {4};
    // 指定初始化器(designated initializer)
    quantity q = {.weight=1.5};
    // 点表示法
    quantity q;
    q.volume = 3.7;
```
无论用哪种方法设置联合的值，都会保存一条数据。联合只是提供了方法。
