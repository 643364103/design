简单工厂模式（Simple Factory）
===
由一个工厂对象决定创建出哪一种产品类的实例.
专门定义一个类来负责创建其他类的实例，被创建的实例常常具有共同的父类.

![alt text](images/1.png '')

### 场景
创建单一的对象
***
````js

//alert
var LoginAlert=(function(){
    class LoginAlert {  
        constructor(text) {
            this.text = text;
        };
        show(){  
            //do  
            console.log(this.text);
        };        
    };
    return LoginAlert;
})();
var nickNameAlert=new LoginAlert('昵称不合法！');
nickNameAlert.show();

//confirm
var LoginConfirm=(function(){
  class LoginConfirm{
    constructor(text){
      this.text=text;
    };
    show(){
      //do
      console.log(this.text);
    };
  };
  return LoginConfirm;
})();
var nameConfirm=new LoginConfirm('你的用户名不存在！','Confirm:');
nameConfirm.show();
````

***
````js
//simple factory
var LoginPopFactory=(function(){
  class LoginPopFactory{
    constructor(name,text){
      switch(name){
        case 'Alert':
           return new LoginAlert(text);
        case 'Confirm':
        default:
           return new LoginConfirm(text);
      }
    };

  };
  return LoginPopFactory;
})();
var nameConfirm=new LoginPopFactory('Confirm','你的用户名不存在！');
nameConfirm.show();
````
思考：
优缺点各个什么？
