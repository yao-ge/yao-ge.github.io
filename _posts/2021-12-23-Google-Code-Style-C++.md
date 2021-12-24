---
layout: post
titile: Google Code Style C++
---

> some personal notes when reading google code style

- [头文件](#头文件)
    - [self-contained头文件](#self-contained头文件)
    - [define保护](#define保护)
    - [前置声明](#前置声明)



a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
a     
# 头文件

## self-contained头文件

> 头文件应该能够自给自足，self-contained，可以作为第一个头文件被引入   

如果.h文件声明了一个模板或者内联函数，同时也在该文件加以定义  
例外：如果某函数模板为所有相关模板函数显式实例化，或者本身是某个类的一个私有成员，那么就只能定义在实例化该模板的.cc文件

## define保护

> 所有头文件都应该使用#define来防止头文件被多重包含，格式：\<PROJECT>\_\<PATH>\_\<FILE>\_H_

为保证唯一性，头文件的命名应该基于所在项目源代码树的全路径

## 前置声明

> 尽可能地避免使用前置声明，使用#include 包含需要的头文件即可

前置声明(forward declaraion)是类、函数和模板的纯粹声明，没有定义
* 优点:节省编译时间，#include会使代码因为头文件中无关的改动重新编译多次
* 缺点:
    - 隐藏了依赖关系，头文件改动时，用户的代码会跳过必要的重新编译过程;
    - 可能会被库的后续更改破坏
    - 来自命名空间std::的symbol时，行为为定义
    - 很难判断什么时候该用前置声明，什么时候用#include
