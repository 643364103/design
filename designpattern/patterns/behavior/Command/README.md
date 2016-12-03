命令模式
====
用于将一个请求封装成一个对象，从而使你可用不同的请求对客户进行参数化
### 代码
````js
var CanvasCommand=(function(){
  var canvas=document.getElementById('canvas'),
  ctx = canvas.getContext('2d');
  //内部命令集对象
  var Action = {
    fillStyle : function(c) {
      ctx.fillStyle = c;
    },
    fillRect :function(x,y,w,h) {
      ctx.fillRect(x,y,w,h);
    },
    moveTo :function(x,y) {
      ctx.moveTo(x,y);
    },
    lineTo :function(x,y) {
      ctx.lineTo(x,y);
    }
  }
  return {
    excute : function(msg){
      if(!msg) {
        if(msg.length){
         for(var i=0,len=msg.length;i<len;i++) 
           arguments.callee(msg[i]);
        }else{
          ms.param = Object.prototype.toString.call(msg.param)==="[object Array]"?msg.param : [msg.param];
          Action[msg.command].apply(Action,msg.param);
        }
      }
    }
  }
})();

CanvasCommand.excute([
{command:'fillStyle',param :'red'},
{command:'fillRect',param :[20, 20, 100, 100]}
]);
````