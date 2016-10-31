多态
===
一个接口，多种实现。同一种事物表现出的多种形态。
### 例子
有一个函数**叫某个人来吃饭**，函数的参数:**人的对象**，可是来了一个**美国人**，你看到的可能是用**刀**和**叉子**在吃饭，而来了一个**中国人**你看到的可能是用**筷子**在吃饭，这就体现出了**同样是一个方法**，可以却产生了**不同的形态**！
***
下面是另一个例子
````js
var Animal=(function(){
    var privateString='private';

    class Animal{  
        constructor(animal) {
            this.animal = animal+privateString;
        };
        eat(){
            var len=arguments.length;
            switch(len){
              case 0:
              default:
                  console.log(this.animal+'在吃草');
                  break;
              case 1:
                  console.log(this.animal+'吃'+arguments[0]);
                  break;
            }  

        };
        get animal(){
            return this._animal.toUpperCase();
        };
        set animal(animal){
            this._animal=animal;
        };
    };
    return Animal;
})();
var cow = new Animal("cow");
cow.eat();
cow.eat('树叶');
````
