+++
draft = false
date = 2018-09-06T12:27:47+08:00
title = "C++ Virtual Table"
slug = ""
tags = []
categories = []
+++

### 内存

https://www.cnblogs.com/wangxiaobao/p/5850949.html

<pre><c>class A {
public:
    virtual void vfunc1();
    virtual void vfunc2();
    void func1();
    void func2();
    virtual ~A();
private:
    int m_data1, m_data2;
}; 

class B : A {
public:
    virtual void vfunc1();;
    void func2();
    virtual ~B();
private:
    int m_data3;
};

class C : B {
public:
    virtual void vfunc1();
    void func();
private:
    int m_data1, m_data4;
};
</c></pre>