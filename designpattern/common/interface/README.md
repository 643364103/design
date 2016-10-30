JavaScript 接口的实现方式

````js
var Interface = function(name,motheds){
    if(agruments.length!=2){
        throw new Error("Interface constructor called with "+arguments.length+"arguments,but expected exactly 2");
    }
    this.name = name;
    this.methods = [];
    for(var i=0;i<motheds.length;i++){
        if(typeof motheds[i] !== 'string'){
            throw new Error('Interface constructor expects mothed names to be'+'passes in as a string');
        }
        this.methods.push(motheds[i]);
    }
}
Interface.prototype.ensureImplements = function(objs){
    if(agruments.length != 1){
        throw new Error("Interface constructor called with "+arguments.length+"arguments,but expected exactly 1")
    }
    for(var i=0;i<objs.length;i++){
         var obj = objs[i];
         for(var j=0;j<this.motheds.length;j++){
               var mothed = this.methods[j];
               if(!obj[mothed] || !typeof obj[mothed] !== 'function'){
                    throw new Error('Function Interface.ensureImplements:implements interface'+this.name+',obj.mothed'+mothed+'was not found');
               }
         }
    }
}
````
