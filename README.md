## 《十分钟快速入门CSS》

这是一本介绍CSS的入门小书，内容丰富简短，带您快速入门CSS。

### 目录
* [内嵌样式](#内嵌样式)
* [样式标签](#样式标签)
* [ID名](#ID名)
* [Class名](#Class名)
* [宽度、高度、颜色](#宽度、高度、颜色)
* [边框与文本](#边框与文本)
* [背景](#背景)
* [外边距](#外边距)
* [内边距](#内边距)
* [盒子模型](#盒子模型)
* [块与内联](#块与内联)
* [浮动](#浮动)
* [解决浮动Bug](#解决浮动Bug)
* [定位与层级](#定位与层级)

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
    <div style="width: 100px; height: 100px; color: red; 
    background-color: green; font-size: 20px; font-weight: bold; 
    line-height: 20px; text-align: center;">
    大量堆积内嵌样式
    </div>
    ```

    **[回到目录](#目录)**


###内嵌样式

    style标签用于在HTML标签之外进行样式编写，并且style标签可以放置在
    HTML的任何位置。

    样式标签可以在一定程度上减少内嵌样式的带来的体积冗余问题，样式标签由
    成对的style标签组成，并通过HTML标签名来调用样式我们可以在HTML中任
    何位置编写style标签，书写格式如下例：

    ```
    <style>
        div{
            color: red;
        }
    </style>
    <div>Hello World !</div>   
    ```

    但是通过HTML标签名去实现样式调用会带来一些问题，比如说无法区分不同
    的标签调用不同的样式(在公共样式中编写多个同属性样式时，后面的样式会
    覆盖前面的),例：

    ```
    <style>
        div{
            color: red;
        }

        div{
            color: blue;
        }
    </style>

    <div>test_01</div>
    <div>test_02</div>
    ```

    **[回到目录](#目录)**

###样式标签

    在样式中我们可以通过id去管理不同标签所对应的样式属性，格式和通过标
    签管理样式类似，但是要在HTML标签上添加ID名，（ID名对应唯一的标签，
    调用时以#开头，ID名结尾）例： 

    ```
    <style>
        #test{
            color: red;
        }
    </style>
    <div id="test">
        Hello World !
    </div>
    ```

    ID名具有唯一性（即每个标签对应一个ID），这种特性使得以ID命名不容易
    被共享，极易造成代码冗余。

    **[回到目录](#目录)**

###ID名

    **[回到目录](#目录)**

###Class名

    **[回到目录](#目录)**

###宽度、高度、颜色

    **[回到目录](#目录)**

###边框与文本

    **[回到目录](#目录)**

###背景

    **[回到目录](#目录)**

###外边距

    **[回到目录](#目录)**

###内边距

    **[回到目录](#目录)**

###盒子模型

    **[回到目录](#目录)**

###块与内联

    **[回到目录](#目录)**

###浮动

    **[回到目录](#目录)**

###解决浮动Bug

    **[回到目录](#目录)**

###定位与层级

**[回到目录](#目录)**


