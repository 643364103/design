工厂方法模式（Factory Method）
===
一个创建产品对象的工厂接口，让子类决定实例化哪一个类，将实际创建工作推迟到子类当中
![alt text](images/2.gif '')
### 场景
轻松创建多个类的实例对象，避免了使用者与对象类间的耦合。
***
学科书本的广告简介
````js
//广告数据


//用工厂方法模式（加上了安全保证）
var Factory=function(type,content){
    if(this instanceof Factory){
        return new this[type](content);
    }
    else{
        return new Factory(type,content);
    }
}
Factory.prototype={
    JavaScript:function(content){
                   (function(content){
                       console.log('javascript');
                       var div=document.createElement('div');
                       div.innerHTML=content;
                       div.style.color='red';
                       document.body.appendChild(div);
                   })(content);
    },
    Php:function(content){
            (function(content){
                console.log('Php');
                var div=document.createElement('div');
                div.innerHTML=content;
                div.style.color='blue';
                document.body.appendChild(div);
            })(content);
    }
}
//调用
var data=[{type:'JavaScript',content:'this is JavaScript'},
          {type:'Php',content:'this is Php'}];
for(var i=0,len=data.length;i<len;i++){
    Factory(data[i].type,data[i].content);
}
````
