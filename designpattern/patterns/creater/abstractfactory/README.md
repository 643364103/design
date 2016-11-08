抽象工厂模式（Abstract Factory）
===
创建的结果不是一个真实的对象实例，而是一个类簇，它制定了类的结构。

![alt text](images/1.gif '')

场景：

一个继承体系中，如果存在着多个等级结构（即存在着多个抽象类），并且分属各个等级结构中的实现类之间存在着一定的关联或者约束，就可以使用抽象工厂模式
````js
var VehicleFactory=function(subType,superType){
    //判断抽象工厂中是否存在该抽象类
    if(typeof VehicleFactory[subType] === 'function'){
        //缓存类
        function F();
        //继承父类的属性与方法
        F.prototype=new VehicleFactory[superType]();
        //将子类的constructor指向子类
        subType.constructor=subType;
        //子类的原型继承“父类”
        subType.prototype=new F();
    }
    else {
        throw new Error('未创建该抽象类');
    }
}
//小汽车
VehicleFactory.Car=function(){
    this.type='car';
};
VehicleFactory.Car.prototype={
    getPrice:function(){
        return new Error('抽象方法不能调用');
    },
    getSpeed:function(){
        return new Error('抽象方法不能调用');
    }
};
//公交车
VehicleFactory.Bus=function(){
    this.type='bus';
};
VehicleFactory.Bus.prototype={
    getPrice:function(){
        return new Error('抽象方法不能调用');
    },
    getPassengerNum:function(){
        return new Error('抽象方法不能调用');
    }
}
````
***
````js
var BMW= function(price,speed){
    this.price=price;
    this.speed=speed;
}
VehicleFactory(BMW,'Car');
BMW.prototype={
    getPrice:function(){
        return this.price;
    },
    getSpeed:function(){
        return this.speed;
    }
};
var YUTONG= function(price,passenger){
    this.price=price;
    this.passenger=passenger;
}
VehicleFactory(YUTONG,'Bus');
YUTONG.prototype={
    getPrice:function(){
        return this.price;
    },
    getPassengerNum:function(){
        return this.passenger;
    }
};
````
### 工厂模式总结
> 三种工厂模式极为相似，目的都是为了解耦。

> 相互的演变很容易。

> 在使用时，只需关心是否达到你解耦的效果
