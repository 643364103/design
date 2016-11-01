单一职责（Single Responsibility Principle）
=====================================
### 定义
 一个类只负责一项职责，尽量不要存在多个导致类变更的因素。
### 问题由来
 类T负责两个不同的职责：职责P1，职责P2。当由于职责P1需求发生改变而需要修改类T时，有可能会导致原本运行正常的职责P2功能发生故障。
### 解决方案
分别建立两个分类T1,T2，T1完成P1，T2完成P2

### 最好理解的原则，主要发生在当需求变更时，很容易发生[职责扩散]

### 代码
````js
//ES6的class与getter,setter
class Animal{  
    constructor(animal) {
        this.animal = animal;
    };
    eat(){  
        console.log(this.animal+"是吃草地");  
    };
    get animal(){
        return this._animal.toUpperCase();
    };
    set animal(animal){
        this._animal=animal;
        //this.animal=animal;
    };
}
var cow = new Animal("cow");
cow.eat();
var sheep = new Animal("sheep");
sheep.eat();

````
***
### 思考
1. 如果后面加了食肉的动物carnivore,herbivore
1. 上面的console分别输出什么？
