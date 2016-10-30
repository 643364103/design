#PaGamO 技术沟通

## overall
** <font color="#FF0000">以下所有的API相关只是示意，具体的等确定方案后完成</font>**

+ 页面地址 https://pagamo.101.com/player/index.html?token=&qid=这里是习题的GUID
+ 下图中白色区域为qtiPlayer完成
![alt text](images/1.jpg '')
##前端作答交互时序图
![alt text](images/2.jpg '')

## 方案一 
主要技术：iframe + winodw.postMessage  (IE8以上) ，更好的跨平台

## 方案二
主要技术：Bridge,也可跨平台，但是需要PaGamO去实现三个平台的Bridge。 用户体验会好一点

## 前端交互业务场景API
### qtiPlayer 加载回调通知PaGamO，同时把选项的个数丢过去
> qtiPlayer---->PaGamO
````javascript
{'type':'loaded','data':{}}
````
### PaGamO 送出答案命令至 qtiPlayer 
> PaGamO---->qtiPlayer
````javascript
{'type':'confirmAnswer'};
````
### qtiPlayer 送出答题情况 至 PaGamO 
> qtiPlayer---->PaGamO
````javascript
{'type':'Answer','data':{}};
````
### PaGamO 题目解析命令至 qtiPlayer 
> PaGamO---->qtiPlayer
````javascript
{'type':'showHint','data':{}};
````
### PaGamO 时间计时结束至 qtiPlayer 
> PaGamO---->qtiPlayer
````javascript
{'type':'timeout','data':{}};
````
## 后端
### 获取用户作答情况 http get 
> PaGamO  API地址：https://pagamo.101.com/history
### 存储用户作答情况 http Post
> qtiPlayer API地址：https://pagamo.101.com/post


