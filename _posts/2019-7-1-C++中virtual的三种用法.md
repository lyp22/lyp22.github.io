---
published: true
title: C++中virtual的三种用法
category: C++
tags: 
  - C++
layout: post
---


# virtual用法一：

'''
#include<iostream> 
using namespace std;
class A{
public:
     virtual  void  display(){  cout<<"A"<<endl; }
     };
class B :  public A{
public:
            void  display(){ cout<<"B"<<endl; }
     };
void doDisplay(A *p)
{
    p->display();
    delete p;
}
 
int main(int argc,char* argv[])
{
    doDisplay(new B());
    return 0;
}
'''

这段代码打印出的结果为B，但是当把A类中的virtual去掉之后打印出的就为A。当基类中没有virtual的时候，编译器在编译的时候把p看做A类的对象，调用的自然就是A类的方法。但是加上virtual之后，将dispaly方法变成了虚方法，这样调用的时候编译器会看调用的究竟是谁的实例化对象，这样就实现了多态的效果。也就是说，当基类的派生类中有重写过基类的虚方法的时候，使用基类的指针指向派生类的对象，调用这个方法实际上调用的会是派生类最后实现的方法。

# virtual用法二:

'''
#include<iostream> 
using namespace std;
class Person{
   public:    Person(){ cout<<"Person构造"<<endl; }
           ~Person(){ cout<<"Person析构"<<endl; }
};
class Teacher : virtual public Person{
   public:    Teacher(){ cout<<"Teacher构造"<<endl; }
            ~Teacher(){ out<<"Teacher析构"<<endl; }
};
class Student : virtual public Person{
  public:      Student(){ cout<<"Student构造"<<endl; }
             ~Student(){ cout<<"Student析构"<<endl; }
};
class TS : public Teacher,  public Student{
public:   TS(){ cout<<"TS构造"<<endl; }
          ~TS(){ cout<<"TS析构"<<endl; }
};
int main(int argc,char* argv[])
{
    TS ts;
    return 0;
}
'''

这段代码的终端输出结果为： 

'''
Person构造 
Teacher构造 
Student构造 
TS构造 
TS析构 
Student析构 
Teacher析构 
Person析构 
'''

当Teacher类和Student类没有虚继承Person类的时候，也就是把virtual去掉时候终端输出的结果为： 

'''
Person构造
Teacher构造
Person构造
Student构造
TS构造
TS析构
Student析构
Person析构
Teacher析构
Person析构
'''

大家可以很清楚的看到这个结果明显不是我们所期望的。我们在构造TS的时候需要先构造他的基类，也就是Teacher类和Student类。而Teacher类和Student类由都继承于Person类。这样就导致了构造TS的时候实例化了两个Person类。同样的道理，析构的时候也是析构了两次Person类，这是非常危险的，也就引发出了virtual的第三种用法，虚析构。

# virtual用法三:

'''
#include<iostream>
using namespace std;
class Person{
 public:        Person()  {name = new char[16];cout<<"Person构造"<<endl;}
      virtual  ~Person()  {delete []name;cout<<"Person析构"<<endl;}
 private:
         char *name;
         };
class Teacher :virtual public Person{
public:         Teacher(){ cout<<"Teacher构造"<<endl; }
              ~Teacher(){ cout<<"Teacher析构"<<endl; }
};
class Student :virtual public Person{
public:         Student(){ cout<<"Student构造"<<endl; }
              ~Student(){ cout<<"Student析构"<<endl; }
};
class TS : public Teacher,public Student{
public:             TS(){ cout<<"TS构造"<<endl; }
                 ~TS(){ cout<<"TS析构"<<ENDL; }
};
int main(int argc,char* argv[])
{
Person *p = new TS();
delete p;
return 0;
}
'''

这段代码的运行结果为：

'''
Person构造
Teacher构造
Student构造
TS构造
TS析构
Student析构
Teacher析构
Person析构
'''

但是当我们把Person类中析构前面的virtual去掉之后的运行结果为：

'''
Person构造
Teacher构造
Student构造
TS构造
Person析构
程序崩溃
'''

很明显这个结果不是我们想要的程序，崩溃造成的后果是不可预计的，所以我们一定要注意在基类的析构函数前面加上virtual，使其变成虚析构在C++程序中使用虚函数，虚继承和虚析构是很好的习惯 可以避免许多的问题。

