# 代码
## 编译器与连接器
### 定义可在其他文件中，使用函数前必须声明。
### 定义则存在body，声明甚至可以省略命名传参，但必须指定类型。如图
![alt text](image.png)

![alt text](image-1.png)
## 预处理
### vs中可以直接显示预处理后的文件
### 编译器通过预处理后的文件判断代码是否能够正常编译
### **头文件**就是把文本粘贴过来。如图，编译通过，输出正确
![alt text](image-2.png)
### `#define`语句，遍历搜索并全部替换字符串，如图编译通过，输出正确
![alt text](image-3.png)
### `#if` `#endif` 语句
![alt text](image-4.png)
## 变量
### 所有类型都是让生活变得更好的一种方式，它的本质仍是数据
### 数据类型的区别只在于创建时分配内存的多少，并不一定规定所需表示的意义
### int 整型
#### 4byte即32位二进制数来表示一个数字，即最大值为±2^31
#### 使用unsigned修饰可略去符号位，表示32位二进制正数
#### 字符与数字没有区别，通过asc码转换。
- **`char`** 1 byte 数字
*在控制台输出中,自动将char类型的数字转换为字符串*
- **`short`**  2 byte
- **`long`** 4 byte
- **`long long`** 8 byte
- **`float`** 4 byte
- **`double`** 8 byte
- **`bool`** 1 byte
- **`const char*`** 字符串
> 可以直接使用如`2.5f`来定义单精度浮点
> 除了0以外的任何数字都表示true
### 指针 
- 在定义的变量类型后添加`*`
### 引用
- 在定义的变量类型后添加`&`
![alt text](image-5.png)
## 头文件
### 用于声明函数，并在各个cpp文件中include
### c++标准库头文件一般不包含扩展名，包含扩展名的为c标准库
### 读取内存
## 条件和分支
- `if`
- `else`
- `if else`
## setupProject
### 分清filter和folder
## 循环 loops
### for循环
#### 三个参数
- 变量声明,刚开始循环运行一次。(可以缺省，只需将i在循环前声明)
- 循环条件
- 下次循环发生前执行的代码
> `for (int i = 0; i < 5; i++){}`
#### 三个参数都可以缺省，发挥想象
### while循环
#### 一个参数(循环条件)
> `while (i<5){}`
### do while
#### 一个参数(循环条件)
#### 在判断条件前先执行一遍代码
```c
do{}
while(condition);
```
## 流程控制
### `return`
> 结束当前函数并返回值
### `break`
> 循环结束，跳出整个循环
### `continue`
> 跳转到for循环的下一次迭代。结束本次循环，并执行for的第三个参数
 
## 指针
### 所有指针都是一个int整数，存储内存地址的数字 1byte
### 原始指针 raw_point
- `void*`无类型指针
- `&变量名`返回变内存地址,即指针
- `*指针名`逆向引用指针,即访问内存地址指向的变量数据，可以读写
![alt text](image-6.png)
## 引用
### 使用：类型加上&
### 定义一个虚拟变量，如
```c
int a = 114514;
int& b = a;
```
<details>

<summary>🌰栗子</summary>

### 当我们想调用函数实现变量自增时，可能写出如下代码，而实际输出为5

```c
   void increase(int aaa) {
    aaa++;
}
int main()
{
    int var = 5;
    increase(var);
	std::cout << var << std::endl;
}
```
### 可以通过以下代码实现
```c
void increase(int* aaa) {
    (*aaa)++;
}
int main()
{
    int var = 5;
    increase(&var);
	std::cout << var << std::endl;
}
```
### 最优解为使用 引用
```c
void increase(int& aaa) {
    aaa++;
}
int main()
{
    int var = 5;
    increase(var);
	std::cout << var << std::endl;
}
```
</details>


### 与函数别名类似，即变量别名。
### 声明一个引用时必须赋值，且之后不能更改引用的对象。如果你需要改变，请使用指针，具体参考上述代码中的第二种方式
## 类 class
### 来写一个logger
- 设置输出等级
- 输出入口
## 结构体 struct
## static
### 在类和结构外部
#### 使用static使变量只会在该cpp文件中产生链接
#### 而使用extern则效果相反
#### 在头文件中声明变量时作用挺大
### 在结构体内
#### 被static修饰的变量将作为该类下的全局变量。任意实例下的修改将作用在全体实例上，即对player1的修改，同时作用在player23456身上
#### 使用结构体内部的静态对象前，必须声明
## 内建函数
### 默认情况下，类的成员是私有的，而结构体是公有的
### struct多使用在存储单一数据时使用。
- `sizeof` 内存大小(byte)