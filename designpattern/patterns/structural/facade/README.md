外观模式（facade）
===
为一组复杂的子系统接口提供一个更为高级的统一接口，使得对接子系统的访问更容易。套餐饭~~~~
![alt text](images/1.gif '')
### 例子
````js
var getEvent=function(event){
  return event || window.event;
}
````
***
````js
var A={
  g : function(id){
    return document.getElementById(id);
  },
  css : function(id,key,value){
    document.getElementById(id).style[key]=value;
  }
}
````
