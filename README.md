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


### 样式标签

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

### ID名

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


### Class名

在样式中我们可以利用class名来实现样式共享，class命名与ID命名类似，
区别在于class命名不具有唯一性，允许被重复使用，并且可以实现多命名。 
class命名结构以点开始命名结尾，例： 

```
<style>
    .test01{
    color: red;
    }

    .test02{
    font-size: 20px;
    }
</style>

<div class="test01 test02">
    Hello World !
</div>
```

命名方式还有很多，为了不误导大家，我们留在在本系列的后期再着重讨论。  

**[回到目录](#目录)**

### 宽度、高度、颜色

从本小节开始讲解网页中常用的基础样式，
px（像素）：是网页中常用的长度单位
width（宽度）：用于设置样式的宽度属性
height(高度)：用于设置样式的高度属性
color(颜色)：用于设置样式的字体颜色 

color在设置字体颜色的时候，可以使用英文单词表示颜色的值，也可以用
颜色编码表示字体的色值，例如：color：#000000；（#000000表示黑色）

```
<style>
div{
    width: 100px;
    height: 100px;
    color: red;
}
</style>
<div>
Hello World !
</div>
```

width, height用于设置div的宽高，但是因为目前div为透明色，所以看不
出任何效果，只有字体颜色发生了改变。

width、height的单位也可以使用100%、auto:

100%表示宽度或者高度与父亲容器的宽高相等
auto表示宽度或者高度未设定（此处涉及场景后期会
用实例详细解释）

**[回到目录](#目录)**

### 边框与文本

border：定义标签的边框，（边框属性值有多个例如：边框的样式、边框的粗
细、边框的颜色等）
line-height：定义（块）标签中文字的行高，如果行高恰好与HTML标签高度
相等，则表示文字在HTML标签中居中。
text-align：用于设置文本在水平方向的排版
参数值有：
    1. 文本居左
    2. 文本居中
    3. 文本居右

```
<style>
.test1{
    width: 100px;
    height: 40px;
    line-height: 40px;
    text-align: center; 
    color: red;
    border-width: 1px; /* 边框粗细 */
    border-color: blue; /* 边框颜色 */
    border-style: dashed; /* 边框样式（是实线、虚线等） */
}
</style>

<div class="test1">
Hello World !
</div>
```    

关于简写：
样式允许简写，例如涉及border的多个属性，我们可以用以下方式进行简写，以
减少代码冗余，例：

```
<style>
    .test2{
    width: 100px;
    height: 40px;
    line-height: 40px;
    color: red;
    border: 1px solid #000; 
    /*
    以上简写含义如下：
    border-width: 1px;
    border-style: solid;
    border-color: #000;
    */
    }
</style>

<div class="test2">
简写测试
</div>
```

**[回到目录](#目录)**

### 背景

background用于表示（块）标签的背景，背景的属性值有很多，例：背景颜色、
背景图片、背景平铺状态、背景尺寸等。

```
<style>
.test01{
    width: 100px;  
    height: 100px;
    background-color: black; 
}
</style>

<div class="test01"></div>
```

以下示例用于在（块）标签中引入背景图片background-image: url('图片地
址'); 

```
<style>
    .test02{
        width: 200px;
        height: 200px;
        background: url("test.gif");
    }
</style>
<div class="test02"></div>
```

在背景图大小小于标签大小的情况下，背景图会自动平铺，直到铺满为止。如果想
认为干涉样式的自动平铺行为，我们可以使用以下属性，进行控制。
background-repeat: no-repaet; 
no-repat表示不平铺，在不设置平铺状态的情况下，背景图自动平铺。

```
<style>
    .test03{
        width: 200px;
        height: 200px;
        background: url("test.gif");
        background-repeat: no-repaet; 
    }
</style>
<div class="test03"></div>
```

我们还可以利用以下属性用于设置图片位置
横向位置可以用像素，进行位置偏移，或者使用状态进行控制。
横向：（left、center、right）
纵向：（top、center、bottom）

```
<style>
    .test04{
        width: 200px;
        height: 200px;
        background: url("test.gif");
        background-repeat: no-repaet; 
        background-position: left center; /* x、y位置用空格进行分隔 */
    }
</style>
<div class="test04"></div>  
```

如果当前图片尺寸远小于标签大小，但又不愿意平铺，我们可以使用size属性进行调整，
例：
background-size:(cover,contain)
        
    cover：会拉伸背景图，直到X、Y轴全部铺满标签为止
    contain：会拉伸背景图，直到X或者Y轴铺满为止

```
<style>
    .test05{
        width: 200px;
        height: 200px;
        background: url("test.gif");
        background-repeat: no-repaet; 
        background-size: cover; 
    }
</style>
<div class="test05"></div>   
```

背景图的所有属性都可以进行组合简写
background: url('img') center top/10px 20px  no-repeat;

```
<style>
    .test06{
        width: 200px;
        height: 200px;
        background: url("test.gif") center center/ 20px 30px no-repeat #347623;
    }
</style>
<div class="test06"></div> 
```

在更高级的CSS中（CSS3），样式中的背景允许多图片叠加、同时允许叠加颜色值。

**[回到目录](#目录)**

### 外边距

**[回到目录](#目录)**

### 内边距

**[回到目录](#目录)**

### 盒子模型

**[回到目录](#目录)**

### 块与内联

**[回到目录](#目录)**

### 浮动

**[回到目录](#目录)**

### 解决浮动Bug

**[回到目录](#目录)**

### 定位与层级

**[回到目录](#目录)**


