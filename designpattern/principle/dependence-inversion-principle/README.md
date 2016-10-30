依赖倒置（Dependence Inversion Principle）（面向对象中的面向接口）
================================================
### 定义
抽象不应该依赖细节；细节应该依赖抽象。
### 问题
类A直接依赖类B，假如要将类A改为依赖类C，则必须通过修改类A的代码来达成。这种场景下，类A一般是高层模块，负责复杂的业务逻辑；类B和类C是低层模块，负责基本的原子操作；假如修改类A，会给程序带来不必要的风险。
### 解决方案
改为接口依赖,B,C都依赖接口I，通过接口I发生联系。
### 代码
以计算器为例来说明
````js
//1、从一个加法计算器功能开始。
class Calculator(a,b){
    constructor() {
      this.a= a;
      this.b=b;
    };
    calculate(addition){
        return addition.calculate(this.a,this.b);
    }    
}
class Addition{
     constructor() {

     };
     calculate(a,b){
        return a+b;
     }
}
new Calculator(2,3).calculate(new Addition());
//2、增加需求需要引入减法，我们就需要改动Calcutator.按上面的做法，每加一种都需要改动Calcutator,耦合太高了。
class Subtraction{
     constructor() {

     };
     calculate(a,b){
        return a-b;
     }
}

//我们稍做改变，改成接口依赖[JS的接口实现](common/interface)
//1. 新建一个叫ICalcu 的接口
var ICalculate = new Interface('ICalculate',['calculate']);
//2. 修改Calculator,Addition,Subtraction都实现ICalculate
class Calculator(a,b){
    constructor() {
      this.a= a;
      this.b=b;
    };
    calculate(ICalculate){
        return ICalculate.calculate(this.a,this.b);
    }    
}
class Addition{
     constructor() {
        this.implementsInterfaces = ['ICalculate'];       
     };
     calculate(a,b){
        return a+b;
     }
}
class Subtraction{
     constructor() {
        this.implementsInterfaces = ['ICalculate'];         
     };
     calculate(a,b){
        return a-b;
     }
}
//判断是否实现
ICalculate.ensureImplements(['Addition','Subtraction']);
````
> 针对接口编程，依赖于抽象而不依赖于具体。

> High level modules should not depend upon low level modules.

> Abstractions should not depend upon details.

> Details should depend upon abstractions.
