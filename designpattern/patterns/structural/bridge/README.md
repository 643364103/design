桥接模式 Bridge
===
**桥接模式将抽象部分与它的实现部分分离，是它们都可以独立地变化。**
它很好的支持了开闭原则和组合锯和复用原则。
实现系统可能有多角度分类，每一种分类都有可能变化，那么就把这些多角度分离出来让他们独立变化，减少他们之间的耦合.

![alt text](images/1.jpg '')

桥接模式主要有4个角色组成：

1. 抽象类
1. 扩充抽象类
1. 实现类接口
1. 具体实现类

###案例一分析
````js
var forEach = function (arr, fn) {
    for (var i = 0; i < arr.length; i++) {
        var val = arr[i];
        if (fn.call(val, i, val, arr)) {
            return false;
        }
    }
}
var arr = [1, 2, 3, 4];
forEach(arr, function (i, v) {
    arr[i] = v * 2;
})
````
forEach函数并不关心fn里面的具体实现。fn里面的逻辑也不会被forEach函数的改写影响。
***
### 案例二分析
与单例的结合

````js
var singleton = function( fn ){  
    var result;  
    return function(){  
        return result || ( result = fn .apply( this, arguments ) );  
    };  
};  
var createMask = singleton( function(){  
    return document.body.appendChild( document.createElement('div') );  
});  
````
singleton是抽象部分， 而createMask是实现部分。 他们完全可以独自变化互不影响。 如果需要再写一个单例的createScript就一点也不费力。
````js
var createScript = singleton( function(){  
    return document.body.appendChild( document.createElement('script') );  
});  
````

