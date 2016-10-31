继承的实现
====
### 单继承
***
````js
Object.prototype.extend=function(source){
    for(var property in source){
        this[property]=source[property];
    }
}
````
### 多继承

````js
Object.prototype.mix=function(){
    var arg;
    for(var i=0,len=arguments.length;i<len;i++){
        arg=arguments[i];
        for(var property in arg){
            this[property]=arg[property];
        }
    }
}
````
