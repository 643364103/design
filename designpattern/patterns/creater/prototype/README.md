语言之魂--原型模式（Prototype）
===
用原型实例指向创建对象的类，使用于创建新的对象的类共享原型对象的属性以及方法。
场景：创建复杂的对象时，对于那些需求一直在变化而导致对象结构不停地改变时，将那些比较稳定的属性与方法共用而提取的继承实现。
````js
var LoopImages=function(imgArr,container){
  this.images=imgArr;
  this.container=container;
}
LoopImages.prototype={
  createImage : function(){
    console.log('create');
  },
  changeImage : function(){
    console.log('changeImage');
  }
}
var SlideLoopImg=function(imgArr,container){
  LoopImages.call(this,imgArr,container);
  //private
  this.arrow='private';
}
//继承父类的原型
SlideLoopImg.prototype=new LoopImages();
SlideLoopImg.prototype.changeImage=function(){
  //重写
}
````
````js
//进价
//对象的属性复制，这里只做浅复制，深复制，请见jquery.extends
function prototypeExtend(){
    var F=function(){},
    args=arguments,
    i=0,
    len=args.length;
    for (;i<len;i++) {
       for(var j in args[i]){
           F.prototype[j]=args[i][j];
       }    
    }
    return new F();
}
var fish=prototypeExtend({
    speed:20,
    swim:function(){
        console.log('游泳速度：'+this.speed);
    },{        
        jump:function(){
            console.log('我在跳跃');
    }
});
````
思考：上面两种实现有什么差别？
