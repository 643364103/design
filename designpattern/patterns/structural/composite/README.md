组合模式 Composite
===
组合模式：将对象组合成树形结构以表示“部分-整体”的层次结构，组合模式使得用户对单个对象和组合对象的使用具有一致性。
![alt text](images/1.jpg '')
组合模式主要有三个角色：

1. 抽象组件（Component）：抽象类，主要定义了参与组合的对象的公共接口
2. 子对象（Leaf）：组成组合对象的最基本对象
3. 组合对象（Composite）：由子对象组合起来的复杂对象

理解组合模式的关键是要理解组合模式对单个对象和组合对象使用的一致性，我们接下来说说组合模式的实现加深理解。

### 案例一分析
最简单的组合模式，HTML的DOM结构，addClass 的实现
````js
//jq
$(".test").addClass("noTest").remove("test");
````
模拟一下addClass的实现
````js
var addClass = function (eles, className) {
    if (eles instanceof NodeList) {
        for (var i = 0, length = eles.length; i < length; i++) {
            eles[i].nodeType === 1 && (eles[i].className += (' ' + className + ' '));
        }
    }
    else if (eles instanceof Node) {
        eles.nodeType === 1 && (eles.className += (' ' + className + ' '));
    }
    else {
        throw "eles is not a html node";
    }
}
addClass(document.getElementById("div3"), "test");
addClass(document.querySelectorAll(".div"), "test");
````
对于NodeList或者是Node来说，客户端调用都是同样的使用了addClass这个接口
***
### 案例二分析
产品订单包含多个产品子订单，多个产品子订单组成一个复杂的产品订单。由于Javascript语言的特性，我们将组合模式的三个角色简化成2个角色：

1. 子对象：在这个例子中，子对象就是产品子订单
1. 组合对象：这里就是产品的总订单

假设我们开发一个旅游产品网站，其中包含机票和酒店两种子产品，我们定义了子对象如下：
````js
function FlightOrder() { }
FlightOrder.prototyp.create = function () {
    console.log("flight order created");
}
function HotelOrder() { }
HotelOrder.prototype.create = function () {
    console.log("hotel order created");
}
````
机票订单类和酒店订单类，每个类都有各自的订单创建方法。
接下来我们创建一个总订单类：
````js
function TotalOrders() {
    this.orderList = [];
}
TotalOrders.prototype.addOrder = function (order) {
    this.orderList.push(order);
}
TotalOrders.prototype.create = function (order) {
    for (var i = 0, length = this.orderList.length; i < length; i++) {
        this.orderList[i].create();
    }
}
````
这个对象主要有3个成员：订单列表，添加订单的方法，创建订单的方法。
在客户端使用的时候如下：
````js
var flight = new FlightOrder();
flight.create();

var orders = new TotalOrders();
orders.addOrder(new FlightOrder());
orders.addOrder(new HotelOrder());
orders.create();
````
客户端调用展示了两种方式，一种是单一的创建机票订单，一种是创建多张订单，但最终都是通过create方法进行创建，这就是一个很典型的组合模式的应用场景。
