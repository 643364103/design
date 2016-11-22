享元模式 Flyweight
===
享元模式为运用共享技术有效的支持大量细粒度的对象。因为它可以通过共享大幅度地减少单个实例的数目，避免了大量非常相似类的开销。.
享元模式是一个类别的多个对象共享这个类别的一个对象，而不是各自再实例化各自的对象。这样就达到了节省内存的目的。

在JS中，享元模式主要有下面几个角色组成：

1. 客户端：用来调用享元工厂来获取内在数据的类，通常是应用程序所需的对象，
1. 享元工厂：用来维护享元数据的类
1. 享元类：保持内在数据的类
### 案例一分析
````html
<ul class="menu">
    <li class="item">选项1</li>
    <li class="item">选项2</li>
    <li class="item">选项3</li>
    <li class="item">选项4</li>
    <li class="item">选项5</li>
    <li class="item">选项6</li>
</ul>
````
绑定点击事件，一般用下面的方式绑定
````js
//jq
$(".item").on("click", function () {
    console.log($(this).text());
})
//因为每个项都绑定了事件，都占用了内存。但是这些事件处理程序其实都是很类似的
````
根据事件冒泡原理
````js
$(".menu").on("click", ".item", function () {
    console.log($(this).text());
})
````
### 案例二分析
苹果公司批量生产iphone，iphone的大部分数据比如型号，屏幕都是一样，少数部分数据比如内存有分16G,32G等。
未使用享元模式前，我们写代码如下
````js
function Iphone(model, screen, memory, SN) {
    this. model  = model;//型号
    this.screen = screen;//屏幕
    this.memory = memory;//内存
    this.SN = SN;
}
var phones = [];
for (var i = 0; i < 1000000; i++) {
    var memory = i % 2 == 0 ? 16 : 32;
    phones.push(new Iphone("iphone6s", 5.0, memory, i));
}
````
创建了一百万个iphone，每个iphone都独立申请一个内存.
优化如下：享元类
````js
function IphoneFlyweight(model, screen, memory) {
    this.model = model;
    this.screen = screen;
    this.memory = memory;
}
````
享元工厂
````js
var flyweightFactory = (function () {
    var iphones = {};
    return {
        get: function (model, screen, memory) {
            var key = model + screen + memory;
            if (!iphones[key]) {
                iphones[key] = new IphoneFlyweight(model, screen, memory);
            }
            return iphones[key];
        }
    };
})();
function Iphone(model, screen, memory, SN) {
    this.flyweight = flyweightFactory.get(model, screen, memory);
    this.SN = SN;
}
var phones = [];
for (var i = 0; i < 1000000; i++) {
    var memory = i % 2 == 0 ? 16 : 32;
    phones.push(new Iphone("iphone6s", 5.0, memory, i));
}
console.log(phones);
````
