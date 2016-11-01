依赖倒置（Dependence Inversion Principle）（面向对象中的面向接口）
================================================
### 定义
抽象不应该依赖细节；细节应该依赖抽象。
### 问题
类A直接依赖类B，假如要将类A改为依赖类C，则必须通过修改类A的代码来达成。这种场景下，类A一般是高层模块，负责复杂的业务逻辑；类B和类C是低层模块，负责基本的原子操作；假如修改类A，会给程序带来不必要的风险。
### 解决方案
改为接口依赖,B,C都依赖接口I，通过接口I发生联系。
### 代码
以地图为例来说明
````js
$.fn.myMap = function(options) {
    var defaults = {
        /* defaults */
    };
    options = $.extend({}, defaults, options);
    var mapOptions = {
        center: new google.maps.LatLng(options.latitude,options.longitude),
        zoom: 12
    },
    var map = new google.maps.Map(this[0], mapOptions);    
    return this;
};

$("#map_canvas").myMap({
    latitude: 35.044640193770725,
    longitude: -89.98193264007568
});
````
***
````js
$.fn.myMap = function(options) {
    var defaults = {
        /* defaults */
    };
    options = $.extend({}, defaults, options);
    options.provider.init(this[0],options.latitude,options.longitude)
    return this;
};
var googleProvider=(function(){
    return {
        init:function(container,options){
            var mapOptions = {
                center: new google.maps.LatLng(options.latitude,options.longitude),
                zoom: 12
            },
            var map = new google.maps.Map(container, mapOptions);    
       }
    }
})();
$("#map_canvas").trackMap({
    latitude: 35.044640193770725,
    longitude: -89.98193264007568,
    provider: googleProvider
});
````

> High level modules should not depend upon low level modules.

> Abstractions should not depend upon details.

> Details should depend upon abstractions.
