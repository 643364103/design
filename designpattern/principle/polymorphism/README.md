多态
===
一个接口，多种实现。同一种事物表现出的多种形态。
### 例子
有一个函数**叫某个人来吃饭**，函数的参数:**人的对象**，可是来了一个**美国人**，你看到的可能是用**刀**和**叉子**在吃饭，而来了一个**中国人**你看到的可能是用**筷子**在吃饭，这就体现出了**同样是一个方法**，可以却产生了**不同的形态**！

````js
class Animal{  
    constructor(animal) {
        this.animal = animal;
    };

    eat(){  
        console.log(this.animal+'我是会吃东西的');  
    };
    get animal(){
        return this._animal.toUpperCase();
    };
    set animal(animal){
        this._animal=animal;
    };
};
class Dog extends Animal{
    constructor() {
        super();
    };
    eat() {
		console.log('啃骨头');
	}
	guardHouse() {
		 console.log('看家');
	}
};
class Cat extends Animal{
    constructor() {
        super();
    };
    eat() {
		console.log('吃鱼');
	}
	catchMouse() {
		 console.log('抓老鼠');
	}
};
````
