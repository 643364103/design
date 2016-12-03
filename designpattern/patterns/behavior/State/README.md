状态模式
====
当一个对象的内部状态发生改变时，会导致其行为的改变，这看起来像是改变了对象

### 最简单的状态对象的实现
当我们发现我们的代码有很多的if时，可以考虑
````js
function showResult(result){
  if(result === 0){
    consol.log(0);
  }else if(result === 1){
    consol.log(1);
  }else if(result === 2){
    consol.log(2);
  }else if(result === 3){
    consol.log(3);
  }
}
showResult(2);
````
改进后的代码
***
````js
var ResultState=function(){
  var States ={
    state0:function(){
      console.log(0);
    },
    state1:function(){
          console.log(1);
    },
    state2:function(){
          console.log(2);
    },
    state3:function(){
          console.log(3);
    }
  }
  return {
    show: function(result){
      States['state' + result] && States['state' + result]();
    }
  }
}
````
