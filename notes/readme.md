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