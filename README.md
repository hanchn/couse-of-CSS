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

盒子模型是样式中比较重要的概念，它表示的是标签在网页中所占据的部分空间。
margin表示的是外边距，外边距拥有四个基本属性值
分别是：
   上边距、右边距、下边距、左边距，单位为PX

```
<style>
    .test01{
        width: 100px;
        height: 100px;
        background: red;
        margin: 100px 10px 10px 10px;
    }
</style>

<div class="test01"></div>
```  

我们发现以上示例中的HTML标签位置在网页中发现了偏移，说明外边距已经发生
了作用。
我们在初始化HTML标签的时候，如果不为网页中的标签设置任何边距，网页中的
HTML和body标签也会拥有默认边距，所以为了避免产生混淆，我们在网页加载之
前要记得预先清除所有初始边距。

*：星号选择器，表示选中网页中所有的HTML标签，我们可以利用星号全选选择器，
为网页中的所有标签进行边距的清除。 

```
<style>
    * {
        margin: 0 0 0 0;
    }

    .test2{
        width: 100px;
        height: 100px;
        background: blue;
    }
</style>
<div class="test2"></div>
```

关于简写：
margin属性可以进行简写，
1. 如果margin中的四个参数值相同，我们写一个即可：
    margin: 0 0 0 0; 等同于 margin: 0;
2. 如果margin中的四个参数值成对出现，我们写单对即可：
    margin: 10px 20px 10px 20px; 等同于 margin: 10px 20px;

关于定义：
margin是指HTML标签在网页中所占据的空间大小，而并非是HTML标签在网页中的
偏移，margin空白处无法再放置其他标签。  

关于纵向合并：
如果纵向多标签都存在外边距属性，纵向上的边距并不会叠加，而是会选择最大的
纵向边距进行合并。

```
<style>
.test3{
    width: 100px;
    height: 100px;
    background: green;
    margin:30px;
}

.test4{
    width: 100px;
    height: 100px;
    background: pink;
    margin:80px;            
}
</style>
<div class="test3"></div>
<div class="test4"></div>
```

**[回到目录](#目录)**

### 内边距

padding用于表示内边距，和上一节课所说的外边距类似，但是含义相反。
定义：内边距也是表示HTML标签在网页中所占据的空间大小，但是是指标签内部
的空间。

padding也拥有四个参数值：分别是（上、右、下、左）

例：
父标签（class名为per）内部存在一个子标签
子标签（class名为son）
为了避免子标签贴近父标签，父标签需要将子标签隔开一段距离

```
<style>
    .per{
        width: 200px;
        height: 200px;
        border: 2px solid #000;
        padding: 20px 0 0 0; /* per的上内边距为20px */
    }

    .son{
        width: 50px;
        height: 50px;
        background: red;
    }
</style>

<div class="per">
    <div class="son"></div>
</div>
```

以上示例中，我们可以看到son标签相较于per标签的内部顶边发生了位置的偏移。
padding的作用是让标签内部增加一定的空白空间（此空间不允许其他标签占据）

padding和margin一样，都可以进行简写：
1. 如果padding存在四个相同的参数，可以直接简写成如下：
    padding: 0 0 0 0; 等同于 padding: 0;
2. 如果padding存在四个参数且成对，可以直接简写成如下：
    padding: 0 20px 0 20px; 等同于
    padding: 0 20px; 

**[回到目录](#目录)**

### 盒子模型

盒子模型定义：盒子模型表示HTML标签在网页中所占据的空间大小，这部分空间大
小由外边距、内边距、标签的宽高、边框粗细共同构成，例：

```
<style>
    .box{
        width: 200px;
        height: 200px;
        background: red;
        margin: 10px;
        padding: 10px;
        border: 5px solid #000;
    }
</style>

<div class="box"></div>
```

关于副作用：
    1. 在父标签内部的子标签上使用margin的时候，会产生冒泡行为，导致父标
    签也拥有了子标签的margin值。

    2. 在HTML标签上使用padding属性的时候，因为属性padding是在HTML标
    签上新开辟的空间，所以会使得HTML标签（横向/纵向）变大。
    
    我们在其他小节里会讨论到相关的解决方案。

**[回到目录](#目录)**

### 块与内联

网页中的标签存在两种状态：块标签与内联标签
定义：
    1.块标签可以设置宽度和高度，并默认在横向单独占据一行。
    2.内联标签无法设置宽度和高度，多个内联标签在横向呈队列排列，直到横向空
    间不够，才被迫挤到第二排。  
    3.内联块状标签综合了以上两种标签的特性，既可以设置每个标签的大小，并且
    也能实现横向队列排列。

    我们在示例中使用到的块标签、内联标签、内联块标签分别为（div、span、img）
    ,因为本系列并非HTML教程，我们不对标签含义作详细解释。

```
<style>
    div{
        width: 100px;
        height: 100px;
        background: red;
        margin: 20px;
    }

    span{
        width: 100px;
        height: 100px;
        background: blue;
        margin: 20px;         
    }

    img{
        width: 50px;
        height: 50px;
    }
</style>

<div></div>
<div></div>
<div></div>

<span>测试字体0001</span>
<span>测试字体0002</span>
<span>测试字体0003</span>

<img src="test.gif" alt="">
<img src="test.gif" alt="">
<img src="test.gif" alt="">
```   

如果我们不满意标签的自有块状或者内联特性，我们
可以利用样式进行改造。
display属性用于设置标签的显示状态
    1. block表示块状
    2. inline表示内联
    3. inline-block 表示同时拥有内联和块状特性 

```
<style>
    .test{
        display: inline-block;
    }
</style>

<div class="test"></div>
<div class="test"></div>
<div class="test"></div>
```

**[回到目录](#目录)**

### 浮动

浮动是网页布局中非常重要的一个概念，浮动经常用于控制HTML标签进行横向排列。
因为内联标签本身就是水平横向排列的，所以浮动常用于块状标签，如果在内联标签
上使用浮动，会使得浮动标签隐式转换成块状。
浮动属性拥有两个基本参数值：
float:left; //左浮动
floet:right; //右浮动

```
<style>
    .test01{
        width: 100px;
        height: 100px;
        background: red;
        margin: 20px;
        float: left;
    }
</style>

<div class="test01"></div>
<div class="test01"></div>
<div class="test01"></div>
```

浮动属性在标准的布局中的确产生了“浮动”，因为块标签在网页中各占一行，浮动属
性会强迫HTML标签填充左、右方空白区域。
“浮动”的HTML标签存在一些副作用行为，例：
    1.浮动标签（例如向左浮动）左方未浮动的标签会被浮动标签覆盖
    2.未浮动的父标签中，如果存在子标签，父标签无法被撑开（默认情况下，父标
    签如果不设置高度，父标签的高度与子标签的垂直高度总合相等）
    以下是问题重现示例：


问题1：绿色HTML标签被之前浮动的红色区块覆盖    

```
<style>
    .bro{
        width: 200px;
        height: 200px;
        background: green;
        color: #FFF;
        font-size: 30px;
    }
</style>

<div class="bro">测试被覆盖</div>
```

问题2：父标签无法拥有高度（无法被子标签撑开）

```
<style>
    .per{
        width: 200px;
        height: auto; 
        border: 2px solid #000;
        margin: 100px;
    }

    .son{
        width: 50px;
        height: 50px;
        background: #CCC;
        float: left;
    }
</style>
<div class="per">
    <div class="son"></div>
</div>
```

以上问题的解决办法：
    1. 尝试用inline-block代替float浮动
    2. 为父元素设置固定高度
    然而以上方法，并不适用于所有应用场景，我们在下一节会讲到如何使用其他方式
    解决浮动所带来的问题。

**[回到目录](#目录)**

### 解决浮动Bug

clear属性用于解决浮动所带来的影响，国内很多文章都直译为
清除浮动，其实是不对的，clear并不能清除浮动。 
clear属性拥有三个基本的属性值：
    1. clear:left; // 用于解决来自左侧浮动标签的影响
    2. clear:right; // 用于解决来自右侧浮动标签的影响
    3. clear:both; // 用于解决来自左右两侧浮动标签的影响

```
<style>
.aa{
    width:60px;
    height: 60px;
    background: green;
    border: 2px solid #000;
    float: left;
}

.bb{
    width: 100px;
    height: 100px;
    background: red;
    margin: 10px;
    clear: left;
}
</style>

<div class="aa"></div>
<div class="bb"></div>
```

父标签中浮动的子标签脱离了标准布局流，使得父标签塌陷。所以我们需要把浮动
的标签“围住”，使得父标签能够得到所有子元素的垂直高度。
我们可以为父标签中最后一个子标签添加清除浮动以此来得到垂直高度。

```
<style>
    .per{
        width: 500px;
        height: auto;
        border: 3px solid #000;
    }

    .son{
        width: 100px;
        height: 100px;
        background: red;
        margin: 20px;
    }

    .emp{
        clear: both;
    }
</style>

<div class="per">
    <div class="per"></div>
    <div class="per"></div>
    <div class="per"></div>
    <div class="emp"></div>
</div>
```

注意：
    1.clear作用于元素本身，而并非父标签。
    2.clear并不能清除浮动，只能让标签不受附近浮动标签的影响


**[回到目录](#目录)**

### 定位与层级

定位属性可以打破标准布局流，在网页中任意位置进行布局，配合层级属性可以实现多
层级标签叠加行为。 
定位属性提供了三个属性值（相对定位、绝对定位、固定定位）：
    position: relative;
    position: absolute;
    position: fixed;

定位属性配合：top、right、bottom、left属性进行位置偏移。 

1. 层级
    网页中默认层级关系是写在下面的HTML（定位）标签层级大于之前的HTML（定位）
    标签。
    我们也可以利用index属性进行自定义层级设置

```
<style>
    .aa{
        width: 100px;
        height: 100px;
        background: red;
        position: relative;
    }

    .bb{
        width: 100px;
        height: 100px;
        background: blue;
        position: relative;
        top: -20px;
        left: -20px;
    }
            
</style>

<div class="aa"></div>
<div class="bb"></div>
```    

2. z-index属性可以根据开发者的需求去控制层级，HTML标签的默认层级是0，所以
我们如果想要让其他层级覆盖当前层级，只需要将层级z-index的参数值大于当前层级
数即可。

```
<style>
    .cc{
        width: 100px;
        height: 100px;
        background: red;
        position: relative;
        z-index: 1;
    }

    .dd{
        width: 100px;
        height: 100px;
        background: blue;
        position: relative;
        top: -40px;
        left: -40px;
    }
            
</style>

<div class="cc"></div>
<div class="dd"></div>
```

3. 相对定位能力较弱，具备层级特性，且可以结合偏移属性，进行移动（初始位置为网页
左上角）。
4. 拥有绝对定位属性的标签，浮动属性将失效，可以在网页中任意位置进行位移（初始位
置为网页左上角，如果父标签也具有定位属性，初始位置为父标签左上角）。

```
<style>
    .ee{
        width: 200px;
        height: 200px;
        background: red;
        position: relative;
        left: 100px;
        top: 100px;
        z-index: 1;
    }

    .ff{
        width: 100px;
        height: 100px;
        background: blue;
        position: absolute;
        top: 40px;
        left: 40px;
    }
            
</style>

<div class="ee">
    <div class="ff"></div>
</div>
```

固定定位不受制于任何属性，可以固定在网页“窗口”的任意区域，也可以使用z-index进行
层级设置，并且结合位置属性进行移动，常用于实现锚点跟随，对联广告等功能。

```
<style>
.fixed{
    width: 100px;
    height: 100px;
    position: fixed;
    right: 0;
    bottom: 0;
    background: #000;
}
</style>
        
<div class="fixed"></div>  
```

**[回到目录](#目录)**


