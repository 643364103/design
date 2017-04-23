习题排版问题
===  
## 图文混排  
* http://cs.101.com/v0.1/static/edu_product/esp/questions/65b52b59-a68c-4c6e-a6b6-9deb0b6c8840.pkg/item.xml?_=1492690263062 
* http://cs.101.com/v0.1/static/edu_product/esp/questions/1c5d7dff-b045-4e08-a6ae-68d50bdb407e.pkg/item.xml?_=1492690263891 
* http://cs.101.com/v0.1/static/edu_product/esp/questions/758f5b2c-c4ae-4310-914d-280b61645ac9.pkg/item.xml?_=1492690263899   
* http://cs.101.com/v0.1/static/edu_product/esp/questions/e2e03f8a-5e2a-4c14-bd7a-1758866b3d90.pkg/item.xml?_=1492690263905 
* http://cs.101.com/v0.1/static/edu_product/esp/questions/c1036929-5cea-4172-8f27-a7269ab497b6.pkg/item.xml?_=1492690263910 
* http://cs.101.com/v0.1/static/edu_product/esp/questions/d87993a1-d94c-4269-b90b-2f3260af878e.pkg/item.xml?_=1492690263917   
  * 所有对比的项都放在同一个行内，没有进行换行。（PC端正常）
* http://cs.101.com/v0.1/static/edu_product/esp/questions/fa6eaf54-6ec6-4352-9c35-1b6ab5bf71b8.pkg/item.xml?_=1492690263919   
  * 图片没有跟内容换行，造成填空的内容被图片的高度往下撑。（pc端不正常）
* http://cs.101.com/v0.1/static/edu_product/esp/questions/0f1881da-91f1-4328-b70f-bd63bc48a164.pkg/item.xml?_=1492690263922   
### 分析共性的结果  
* 填空处前后有一个多余的下划线是由于所有的题目中都使用了U这个标签  （pc端不正常）
* 1、2 这两题都存在换行是有4个br 造成换行很高  （pc端不正常）
## 下划线、空格、换行  
* http://cs.101.com//v0.1/static/edu_product/esp/questions/377ce6ed-da1b-4b5d-8c8c-c38b4fdca716.pkg/item.xml?_=1492690263911 
* http://cs.101.com//v0.1/static/edu_product/esp/questions/949dc2c9-870e-4fb8-baac-0b2646877508.pkg/item.xml?_=1492690263916 
* http://cs.101.com//v0.1/static/edu_product/esp/questions/7c866304-40f1-4705-9196-6e2f6276457a.pkg/item.xml?_=1492690263956   
  * 图片没有跟内容换行，造成填空的内容被图片的高度往下撑。（pc端不正常）
* http://cs.101.com//v0.1/static/edu_product/esp/questions/4bbda442-8b16-4b85-8b27-3b976975a6f0.pkg/item.xml?_=1492690264003  
  * 所有对比的项都放在同一个行内，没有有进行换行。（pc端不正常）
* http://cs.101.com//v0.1/static/edu_product/esp/questions/abc5c6e1-f21d-4413-bcef-98ac00c5750c.pkg/item.xml?_=1492693173129 
* http://cs.101.com//v0.1/static/edu_product/esp/questions/eaeb6f93-b961-4c5d-858b-d940a2b468a0.pkg/item.xml?_=1492693173131  
  * 图片img标签设置了固定的宽度，高度
* http://cs.101.com//v0.1/static/edu_product/esp/questions/f42eef2b-c0a3-4df9-b4c1-a0d9469485a1.pkg/item.xml?_=1492693173132  
  * 似乎没有排版问题
* http://cs.101.com//v0.1/static/edu_product/esp/questions/bb19eb21-95fb-4026-966c-61f78d43e1c2.pkg/item.xml?_=1492693173133  
  * 似乎没有排版问题
* http://cs.101.com//v0.1/static/edu_product/esp/questions/94db4431-1da1-428d-98da-d917f36ee99b.pkg/item.xml?_=1492693173136 
* http://cs.101.com//v0.1/static/edu_product/esp/questions/6600cb2f-c6d3-4365-9c38-8c9b3f5cd31b.pkg/item.xml?_=1492693173139 
* http://cs.101.com//v0.1/static/edu_product/esp/questions/35d99cae-2757-491e-878c-828da2ac3cfb.pkg/item.xml?_=1492693173140  
  * 似乎没有排版问题
* http://cs.101.com//v0.1/static/edu_product/esp/questions/31d4741d-01a9-4064-9e67-e7da5f133c4e.pkg/item.xml?_=1492693173141  
  * 似乎没有排版问题
### 分析共性的结果   
* 存在多个换行BR  
* 填空处前后有一个多余的下划线是由于所有的题目中都使用了U这个标签 或 span style="text-decoration: underline;" 
## 字体大小颜色  
* http://cs.101.com/v0.1/static/edu_product/esp/questions/46e1acb7-f388-4839-b671-a2112ea6ce59.pkg/item.xml?_=1492693173149  
  * 似乎没有排版上字体的问题
* http://cs.101.com/v0.1/static/edu_product/esp/questions/31d4741d-01a9-4064-9e67-e7da5f133c4e.pkg/item.xml?_=1492693173163  
  * 似乎没有排版上字体的问题
* http://cs.101.com/v0.1/static/edu_product/esp/questions/66540e34-8238-4071-b012-ec80a954001f.pkg/item.xml?_=1492695168221  
  * 题目数据有写明是黑色#000000
### 分析共性的结果  
  * span里都有声明 style="color:#000000" 或 style="color:#auto" 
## 根据以上的数据的分析得出的结论
* PC端一样存在的问题  
  * 每个填空前后都多出一个下划线 
  * 存在多个换行BR  
  * 图片没有跟内容换行，造成填空的内容被图片的高度往下撑  
  * 字体上的问题
* PC端不存在的问题（假象）  
  * 图片img标签设置了固定的宽度，高度  
  * 所有对比的项都放在同一个行内，没有进行换行。
## 解决方案  
### 刷库
  * 针对以上的共性来看，对可以全局对U的标签，span标签 里包含textEntryInteraction的进行去除U标签的处理  
  * 连续多个br的进行只保留一个br的处理（可能引起其他正常问题的不正常）  
### 编辑器  
  * 新增手机端的预览，让入库确认完后再入库  
  * 题库的审核，加入手机端适配的审核~~~~~~~~~




