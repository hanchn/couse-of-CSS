## 《十分钟快速入门CSS》

这是一本介绍CSS的入门小书，内容丰富简短，带您快速入门CSS。

### 目录

* [内嵌样式]http://www.baidu.com
* 样式标签
* ID名
* Class名
* 宽度、高度、颜色
* 边框与文本
* 背景
* 外边距
* 内边距
* 盒子模型
* 块与内联
* 浮动
* 解决浮动Bug
* 定位与层级

### 内嵌样式

样式定义：用于辅助美化HTML，使得网页效果色彩性更高，更容易吸引用户。
样式可以为网页设置颜色、背景、排版等丰富的属性。

标签中的style属性用于帮助标签定义内嵌样式，内嵌样式格式如下例所示，
使用style作为标记，在内部写入格式如： key:value; 的数据对象来表示
具体的样式。
    
```
<div style="color: red;">
    Hello World !
</div>
```

在标签很多的情况下，如果大量在页面中堆叠内嵌样式，则会使得页面臃肿
冗余，如下例：

```
<div style="width: 100px; height: 100px; color: red; background-color: green; font-size: 20px; font-weight: bold; line-height: 20px; text-align: center;">
大量堆积内嵌样式
</div>
```


