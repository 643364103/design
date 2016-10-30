里氏代换（Liskov Substitution Principle）(继承)
=======================================
### 定义
如果对每一个类型为 T1的对象 o1，都有类型为 T2 的对象o2，使得以 T1定义的所有程序 P 在所有的对象 o1 都代换成 o2 时，程序 P 的行为没有发生变化，那么类型 T2 是类型 T1 的子类型。
> 任何基类可以出现的地方，子类一定可以出现.
### 问题

### 解决方案

### 代码
````js
//ES6
class ClassA{  
    constructor() {
    };
    //两数相减
    foo1(a,b){  
        console.log(a-b);
        return a-b;
    };       
}
//B的需求为 a,b 相加然后再加上123
class  ClassB extends ClassA{
    constructor() {
       //调用父类的constructor
       super();
    };
    foo1(a,b){  
        return a+b;
    };
    foo2(a,b){
        return this.foo1(a,b)+123;
    };
}
var classA = new ClassA();
classA.foo1(2,1);
var classB = new ClassB();
classB.foo2(2,1);
//如这里不小心写错了？？
````
