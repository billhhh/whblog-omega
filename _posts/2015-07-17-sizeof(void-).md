---
layout: post
title: sizeof(void*)
category: c++
comments: true
---

在vs中，Win32 和 X64 的结果不同：
（1）Win32 平台结果是4
（2）X64平台结果是8

只要是指针，不只是void*，包括char* 或 int*，结果都是一样。
原因就是指针存放的是内存地址，所以Win32 索引32位地址（4字节），X64索引64位地址（8字节）
![这里写图片描述](http://img.blog.csdn.net/20150717121939341)

![这里写图片描述](http://img.blog.csdn.net/20150717122035437)

最后给一段干坏事的代码，很简单，但是跟上面说的贴切，用 Win32 指令编译是只能吃掉4G，但是用 X64 就一定可以吃干你的内存 ~.~，原理同上

```c++
#include <iostream>
using namespace std;

int main()
{
	while (1)
		malloc(sizeof(int));
	return 0;
}

```

[本篇csdn博客链接](http://blog.csdn.net/scythe666/article/details/46925689)
