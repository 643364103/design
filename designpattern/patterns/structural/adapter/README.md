适配器模式 Adapter
=============
将一个对象的接品（方法或属性）转化成另外一个接口，以满足用户需求，使对象之间接口的不兼容问题得于兼容。
两个成熟的类需要通信，但是接口不同，由于开闭原则，我们不能去修改这两个类的接口，所以就需要一个适配器来完成衔接过程。

![alt text](images/1.gif '')
### 框架适配例子
````js
var A={
  g : function(id){
    return document.getElementById(id);
  }
}
````

````js
var A={
  g : function(id){
    return $('#'+id).get(0);
  }
}
````
***
### 参数适配
````js
function foo(obj){
  var _adapter={
    age:23,
    color:'black'
  };
  for(var i in _adapter){
    _adapter[i]=obj[i]||_adapter[i];
  }
}
````
***
