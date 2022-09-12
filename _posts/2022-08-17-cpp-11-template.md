---
layout: post
title:  "C++11.类模板和函数模板"
date:   2022-08-16
excerpt: "cpp.类模板和函数模板"
tag:
- C++
- template
comments: false
---

<center><b>C++11.类模板和函数模板.</b> </center>

# C++11.类模板和函数模板



```c++
#include<iostream>
#include<string>

using namespace std;

template<class T1, class T2>
class Person
{
public:
	Person(T1 name, T2 age)
	{
		this->m_Name = name;
		this->m_Age = age;
	}
	void showPerson()
	{
		cout << "name is " <<m_Name<< endl;
		cout << "age is " << m_Age<<endl;
	}
	T1 m_Name;
	T2 m_Age;
};
//指定传入类型
void printPerson1(Person<string,int>& p)
{
	p.showPerson();
}

void test01()
{
	Person<string, int> p("Wang", 100);
	printPerson1(p);
}

template<class T1, class T2>
void printPerson2(Person<T1, T2>& p)//传入Person类模板对象
{
	p.showPerson();
}

void test02()
{
	Person<string, int> p("Li", 90);
	printPerson2(p);
	Person<int, int> p1(1,1);
	printPerson2(p1);
}

template<class T>
void printPerson3(T& p)//传入任意类模板对象
{
	p.showPerson();
}

void test03()
{
	Person<string, int> p("Zhang", 80);
	printPerson3(p);
}
int main()
{
    Person<string,int> p1("abc", 90);
    p1.showPerson();
    Person<int, int> p2(1,90);
    p2.showPerson();

	test01();
	test02();
	test03();
}

```



END