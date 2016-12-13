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
***
超级玛丽
````js
var MarryState=function(){
// 内部状态私有变量
  var _currentState={},
      states={
        jump:function(){
          console.log('jump');
        },
        move:function(){
          console.log('move');
        },
        shoot:function(){
          console.log('shoot');
        },
        jump:function(){
          console.log('jump');
        }
      };
      // 动作控制类
  var Action ={
    changeState :function(){
      // 组合动作通过传递多个参数实现
      var arg=arguments;
      // 重置内部状态
      _currentState={};
      // 如果有动作则添加动作
      if(arg.length)
      {
        // 遍历动作
        for(var i=0,len=arg.length;i<len;i++){
          // 向内部状态中添加动作
          _currentState[arg[i]]=true;
        }
      }
      return this;
    },
    // 执行动作
    goes:function(){
      console.log('go action');
      // 遍历内部状态保存的动作
      for(var i in _currentState){
        //如果该动作存在则执行
        states[i]&&states[i]();
      }
      return this;
    }
  }
  // 返回接口方法，change、goes
  return {
    change:Action.changeState,
    goes:Action.goes
  }
}
````
***
````js
var marry=new MarryState();
marry.change('jump','shoot')
     .goes()
     .goes()
     .change('shoot')
     .goes();
````

###与strategy的区别
1. 一个是实现把对象的内在状态的变化封装起来，用外部行为来表现出来；
1. 一个是封装一系列平行且复杂多变的实现方式，
