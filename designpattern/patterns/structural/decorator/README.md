装饰模式 Decorator
===
装饰模式动态地给一个对象添加一些额外的职责，就增加功能来说，它比生成子类更灵活。也可以这样说，
装饰模式把复杂类中的核心职责和装饰功能区分开了，这样既简化了复杂类，有去除了相关类中重复的装饰逻辑。
装饰模式没有通过继承原有类来扩展功能，但却达到了一样的目的，而且比继承更加灵活，所以可以说装饰模式是继承关系的一种替代方案。
![alt text](images/1.png '')

1. 抽象构件(Component)角色：给出一个抽象接口，以规范准备接收附加责任的对象。
1. 具体构件(ConcreteComponent)角色：定义一个将要接收附加责任的类
1. 装饰角色(Decorator)：持有一个构件(Component)对象的实例，并定义一个与抽象构件接口一致的接口
1. 具体装饰角色(ConcreteDecorator)：负责给构件对象“贴上”附加的责任


Javascript中的对象添加新的属性是一个非常直接了当的过程。
装饰模式解耦了核心和装饰功能，锁业也是强调了松耦合。


### 案例一分析
````js
// 最简单的装饰
function vehicle( vehicleType ){
    this.vehicleType = vehicleType || "car";
    this.model = "default";
    this.license = "00000-000";

}

var testInstance = new vehicle( "car" );
console.log( testInstance );

// Outputs:
// vehicle: car, model:default, license: 00000-000


var truck = new vehicle( "truck" );

//添加新能力
truck.setModel = function( modelName ){
    this.model = modelName;
};

truck.setColor = function( color ){
    this.color = color;
};


truck.setModel( "CAT" );
truck.setColor( "blue" );

console.log( truck );

// Outputs:
// vehicle:truck, model:CAT, color: blue

// Demonstrate "vehicle" is still unaltered
var secondInstance = new vehicle( "car" );
console.log( secondInstance );

// Outputs:
// vehicle: car, model:default, license: 00000-000
````

###　案例二分析
带有多个装饰器的装饰对象
````js
// The constructor to decorate
function MacBook() {

  this.cost = function () { return 997; };
  this.screenSize = function () { return 11.6; };

}

// Decorator 1
function Memory( macbook ) {

  var v = macbook.cost();
  macbook.cost = function() {
    return v + 75;
  };

}

// Decorator 2
function Engraving( macbook ){

  var v = macbook.cost();
  macbook.cost = function(){
    return  v + 200;
  };

}

// Decorator 3
function Insurance( macbook ){

  var v = macbook.cost();
  macbook.cost = function(){
     return  v + 250;
  };

}

var mb = new MacBook();
Memory( mb );
Engraving( mb );
Insurance( mb );

// Outputs: 1522
console.log( mb.cost() );

// Outputs: 11.6
console.log( mb.screenSize() );
````