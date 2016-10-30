封装
===
````js
class Animal{  
    constructor(animal) {        
        this.privateString='private';
        this.animal = animal+this.privateString;
    };
    static hasMetabolism(){
        return true;
    };
    static test=1;
    eat(){  
        console.log(this.animal+"是吃草地");  
    };
    get animal(){
        return this._animal.toUpperCase();
    };
    set animal(animal){
        this._animal=animal;
    };
}
var cow = new Animal("cow");
cow.eat();
cow.privateString;
Animal.hasMetabolism();

//私有变量、方法怎么处理
var Animal=(function(){
    var privateString='private';
    class Animal{  
        constructor(animal) {
            this.animal = animal+privateString;
        };
        eat(){  
            console.log(this.animal+"是吃草地");  
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
cow.privateString;
````
