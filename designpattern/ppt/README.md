````js
需求：
假设有个内衣工厂，目前的产品有50种男式内衣和50种女士内衣，为了推销产品，工厂生产一些塑料模特来穿上他们的内衣拍成广告照片
下面是没有使用享元模式完成，请用享元模式修改下面的代码
var Model =function(sec,underware){  
   this.sex= sex;  
   this.underware= underware;  
}  
  
Model.prototype.takePhoto=function(){  
  console.log('sex='+this.sex+'underwear='+this.underware);  
}  
  
for(vari=1;i<=50;i++){  
   var maleModel=new Model('male','underwear'+i);  
   maleModel.takePhoto();  
}  
  
for(vari=1;i<=50;i++){  
   var femaleModel=new Model('female','underwear'+i);  
    femaleModel.takePhoto();  
}  
//要得到一张照片，每次都需要传入sex和underwear参数，如上所述，现在一共50种男内衣和50种女内衣，所以一共产生100个对象
````
***
````js
//只需要区别男女模特，那我们先把underwear参数从构造函数中移除
var Model = function(sex){  
   this.sex = sex;  
}  
Model.prototype.takePhoto = function(){  
  console.log(‘sex=’+this.sex+’underware=’+this.underwear);  
} 
 var maleModel = new Model(‘male’),femaleModel= new Model(‘male’);  
 //给男模特拍照  
 for(var i=1;i<=50;i++){  
   maleModel.underware = ‘underware’+i;  
   maleModel.takePhoto();  
 }  
 //同理女模特  
 for(var i=1;i<=50;i++){  
   femaleModel.underware = ‘underware’+i;  
   femaleModel.takePhoto();  
 }  
````