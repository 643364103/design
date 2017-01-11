惰性模式
====
减少每次代码执行时的重复性分支判断

### 
````js
var A={
  on:function(el,type,fn){
    if(el.addEventListener){
      el.addEventListener(type,fn,false);
    }else if(el.attachEvent){
      el.attachEvent('on' + type,fn)
    }else {
      el['on' + type]=fn;
    }
  }
}
````
````js
var A={
  on:function(el,type,fn){
    if(el.addEventListener){
      el.addEventListener(type,fn,false);
      A.on=el.addEventListener(type,fn,false);      
    }else if(el.attachEvent){
      el.attachEvent('on' + type,fn);
      A.on=el.attachEvent('on' + type,fn)
    }else {
      el['on' + type]=fn;
      A.on=el['on' + type]=fn;
    }
  }
}
````