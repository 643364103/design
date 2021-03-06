代理模式 Proxy
==========
一个对象不能直接引用另一个对象，所以需要通过代理对象在这两个对象之间起到中介的作用。


![alt text](images/1.gif '')
### 案例分析
假如ABC要送酸奶小妹玫瑰花，却不知道她的联系方式或者不好意思，想委托C去送这些玫瑰.

````js
// 先声明美女对象
var girl = function (name) {
    this.name = name;
};

// 这是ABC
var abc = function (girl) {
    this.girl = girl;
    this.sendGift = function (gift) {
        console.log("Hi " + girl.name + ", dudu送你一个礼物：" + gift);
    }
};

// 大叔是代理
var proxyTom = function (girl) {
    this.girl = girl;
    this.sendGift = function (gift) {
        (new abc(girl)).sendGift(gift); // 替dudu送花咯
    }
};
````
调用方式
````js
var proxy = new proxyTom(new girl("酸奶小妹"));
proxy.sendGift("999朵玫瑰");
````
***
### 代理模式与外观模式的区别
代理的客户对象无法直接访问目标对象，代理对象提供对单独目标对象的访问控制，而外观模式的客户对象可以直接访问子系统中的各个对象，但通常由外观对象提供对子系统个元件功能的简化的共同层次的调用接口。
### 代理模式与适配器的区别
二者都属于一种衔接性质的功能。代理对象和被代理对象的接口是同一个，但是客户没法直接访问被代理者，只能通过代理对象去完成被代理对象的访问。而适配器模式是将多个子系统封装起来，提供一个统一的外部接口，客户只需要使用这个外部接口即可访问对象的子系统了。
### 外观跟适配器的区别
二者都是对显存系统的封装。外观模式定义了一个新的接口，而适配器则是复用了一个原有的接口；适配器是用来适配对象的，而外观则是用来适配整个子系统的。
