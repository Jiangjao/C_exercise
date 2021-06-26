# 第5章课后题目

## 一、问答题
### 1、内含10个元素的下标范围是什么？
0到9

### 2、正确声明以下各个变量:
1)digits是一个内涵10个int类型的数组；
int digits[10];
2)rates是一个内涵6个float类型的数组；
float rates[6];
3)mat 是一个内涵3个元素的数组，而每个元素又是内涵5个整数的数组；
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