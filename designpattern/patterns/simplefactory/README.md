Simple Factory
===
````js
//alert
var LoginAlert=(function(){
    class LoginAlert{  
        constructor(text) {
            this.text = text;
        };
        show(){  
            //do  
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
    };
  };
  return LoginConfirm;
})();
var nameConfirm=new LoginConfirm('你的用户名不存在！');
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
