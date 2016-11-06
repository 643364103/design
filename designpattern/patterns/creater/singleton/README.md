单例模式（Singleton）
===
只允许实例化一次的对象类
````js
//全名空间的方式
var Tool={
  Ajax:{
    get:function(){},
    post:function(){}
  },
  Util:{
    method1:function(){}
  }
}
````
````js
//惰性
var LazySingle=(function(){
  var _instance=null;
  function Single(){
    //公共方法与属性
    return {
      pubMethod:function(){},
      pubProperty:'1'
    }
  }
  //获取单例对象
  return function () {
    if(!_instance){
      _instance=Single();
    }
    return _instance;
  }
})();
````
