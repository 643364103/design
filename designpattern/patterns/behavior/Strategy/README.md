策划模式
====
将定义的一组算法封装起来，使其相互之间可以替换。封装的算法具有一定的独立性，不会随客户端变化而变化。

###代码
折扣
````js
var PriceStrategy=function(){
  var Strategy ={
    return30:function(price){
      return +price + parseInt(price / 100)*30;
    },
    return50:function(price){
      return +price + parseInt(price / 100)*50;
    },
    return80:function(price){
      return +price + parseInt(price / 100)*80;
    },
    return90:function(price){
      return +price + parseInt(price / 100)*90;
    },
  }
  return function(algorithm,price){
    return stragtegy[algorithm] && stragtegy[algorithm] (price)
  }
}();
````
***
表单验证
````js
var InputStrategy=function(){
  var Strategy ={
    notNull:function(value){
      return /\s+/.test(value);
    },
    number:function(value){
      return /^[0-9]+(\.[0-9]+)?$/.test(value);
    }
  }
  return function(type,value){
    value = value.replace(/^\s+|\s+$/g,'');
    return stragtegy[type] && stragtegy[type] (value)
  }
}();
````