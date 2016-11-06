建造者模式（Builder）
===
将一个复杂对象的构建与它的表示分离，使得同样的构建过程可以创建不同的表示。

**各执其职，拆解流程**

![alt text](images/1.jpg '')

场景：
一般产品的建造很复杂，那么请用工厂模式，如果产品的建造更复杂，那么请用建造者模式。

跟工厂模式只是多了一个导演类。
***
````js
//应聘者信息
//人类，有技能，爱好,姓名，工作---Product
var Human=function(param){
  this.skill=param&&param.skill||'保密';
  this.hobby=param&&param.hobby||'保密';
  this.name={};//partA
  this.work={};//partB
}
Human.prototype={
  getSkill : function(){
    return this.skill;
  },
  getHobby : function(){
    return this.hobby;
  }
}
//姓名类，有firstname,secondname---concreteBuilder
var Name=function(name){
  var that=this;
  (function(name,that){
    //setPartA
    that.name=name;
    that.firstName=name.slice(0,name.indexOf(' '));
    that.secondName=name.slice(name.indexOf(' '));
  })(name,that);
}
// 工作类---concreteBuilder
var Work=function(work){
  var that=this;
  (function(work,that){
    //setPartB
    switch (work) {
      case 'code':
        that.work='码农';
        that.workDescript='每天在Bug从中窜'；
        break;
      case 'UE':
      case 'UI':
        that.work='设计师';
        that.workDescript='我天生拥有艺术天赋';
      default:

    }
  })(work,that);
}
//---director
var Person = function(name,work){
  var _person=new Human();
  _person.name=new Name(name);
  _person.work=new Work(work);
  return _person;
}
````
***
1. 整体对象类的拆分会无形中增加了结构的复杂性（对象粒度很小，模块利用率低并且变动不太大，建议还是创建整体的对象）
