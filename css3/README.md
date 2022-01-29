## 引入
- link
- style
- @import


## 继承性
- 文本属性可继承:text-,line-,font-

## 权重
| 选择器 | 权值 |
| :---- | :---- |
| 继承 | 0.1 |
| 标签 | 1 |
| 类,伪,属性类 | 10 |
| id | 100 |
| 行内 | 1000 |
| !important | infinity |

## 常用样式
### 文字样式
- color,font(font-style,[font-variant],font-weight,font-size/line-height,font-family),text-decoration,text-indent,text-align,letter-spacing,word-spacing,vertical-align,white-space,text-overflow
### 列表样式
- list-style(list-style-type,list-style-image,list-style-position)
### 盒子模型
- margin(margin-top,margin-right,margin-bottom,margin-left)
- padding(padding-top,padding-right,padding-bottom,padding-left)
- border(border-width,border-style,border-color),border-top/right/bottom/left[-width/style/color]
- box-sizing: border-box:内减盒子模型--盒子宽度/高度=内容+padding+border ；content-box默认，外扩的--盒子宽度/高度=内容
## 背景
- 背景从padding开始渲染，一直到border。
- background(background-color,background-image,background-position[-x/y],background-repeat,background-origin,background-clip,background-attachment,initial|inherit)
- 百分比设置位置：（盒子宽度/高度-图片宽度/高度）%
- 背景图片和SEO：h1设置标题，h1设置背景(text-indet,overflow:hidden)


## 布局
### 标准文档流
- 文本类内容空白折叠现象；基线（baseline）对齐；超过盒子宽度自动换行
- 标签：块级(独占一行，设置宽高，自动撑满父元素，display:block)和行内级(不占一行，不能设置宽高，margin/padding上下不生效左右生效，display:inline)和行内块元素(可以设置宽高，不占一行排列，margin/padding上下会占空间，display:inline-block，img/textarea/input);;html标签：容器级和文本级
### 浮动(float:left/right/none)
- 浮动元素脱离文档流，不再占有原来位置。但其他盒子内的文本依然会为这个元素让出位置，环绕在周围,内容让出浮动部分，但元素没有让出(文字围绕图片)。
- 不占一行，可设置宽高/margin/padding，不存在上下外边距合并问题，脱离文档流不再占有原来位置，原有占父元素百分比宽度变为包裹内容的宽度，注意清除浮动避免影响后面元素布局（clear:left/right/both）,父元素存在塌陷问题（父元素设置高度;外墙法：在父元素同级添加元素其样式添加clear:both---不能撑起父元素;内墙法：在父元素内部最后添加一个元素并添加clear:both---可以直接撑起父元素(可以使用伪元素);设置父元素浮动：子元素可以撑起父元素;父元素设置行内块：display:inline-block可以撑起父元素并占用位置;overflow:除了visible不能清楚浮动其他值都可以清除浮动---有副作用会隐藏或显示滚动条;封装clearfix类：.clearfix::after{clear:both;display:block;content:""}）
- 浮动元素依次"贴边"：元素脱离文档流按照指定方向移动，遇到父级边界或兄弟边界可以容纳下则贴边显示----不浮动的行内块元素不会贴边只会另起一行
### 定位(position:relative/absolute/fixed/static)
- 除static其余均激活top,left,right,bottom;激活z-index
- 优先级：top>bottom,left>right
- 设置定位的盒子会遮盖没有定位的盒子(包括浮动)；都设置定位，则后面盒子会遮盖前面的盒子；
- relative：相对于元素原有位置的定位；未脱离文档流；left/top优先级高；辅助绝对定位；元素不设置宽高top/left/right/bottom不会影响元素宽高；
- absolute：寻找最近的祖先元素（relative,absolute,fixed）没有则相对于body元素定位；脱离文档流；top根据body左上角定位（不是内容）；bottom相对于屏幕地边定位；元素不设置宽高top/left/right/bottom宽高会自适应；相对于祖先元素padding定点（包含padding）进行定位设置；无论什么元素此时display属性失效（此时类似inline-block）；
- fixed:脱离文档流；只相对于浏览器窗口定位；display属性失效（此时类似inline-block）；元素不设置宽高top/left/right/bottom宽高会自适应
- z-index:父盒子z-index高的无论子盒子设置多少都会在父盒子z-index低的前面


## 伪元素
- 该元素不在文档树中，可为其添加样式，必须设置content属性；
- ::before,::after
- ::first-letter,::first-line,::selection

## 伪类
- :hover,:focus,:link,visited,:active
- :checked：被选中的伪类
- :disabled：不可用的表单元素伪类
- :enabled：可用的表单元素伪类
- :not(selector)：排除伪类，选择非selector元素的伪类
- :target：选择当前活动的元素
- :empty：空节点的伪类
- :only-child：该元素是某个元素的唯一一个儿子的伪类
- 不会出现在文档树中；可以添加到任何选择器的位置，而伪元素只能添加在最后一个简单选择器后面；伪类操作对象是文档树中存在的元素；
- 节点（node）是js中的概念：页面中一切都可以看成是节点，包括元素节点，文本节点，属性节点等

## 单位
- %,px,em,rem;in,cm,mm,pt,pc,ex,vw,vh,vmin,vmax

## FC(Formatting Contexts)
- BFC(Block Formatting Contexts):BFC区域不会与float重叠；容器里的子元素不会影响到外面元素；触发BFC：根元素；float不为none；position为absolute或fixed；display为inline-block,table-cell,table-caption,flex；overflow不为visible；
- IFC(Inline Formatting Contexts)
- GFC(GridLayout Formatting Contexts)
- FFC(Flex Formatting Contexts)

## css3
- border-radius(border-top-left-radius,border-top-right-radius,border-bottom-left-radius,border-bottom-right-radius):像素/百分比
- rgba()(不会影响子元素，opacity会影响子元素),hsl(),hsla()
- box-shadow
- text-shadow(h-shadow,v-shadow,blur,color)
- background-origin(处理背景图片；border-box/content-box/padding-box);background-clip(处理背景色和背景图片；border-box/padding-box/content-box);background-size(处理背景图片；px/%/cover/contain)
- background-image:linear-gradient(direction,color-stop,color-stop1,......)；background-image: radial-gradient(shape size at position, start-color, ..., last-color);
- background:url(),url(),url()......:多背景；background其他属性设置也可以通过`,`分别设置对应背景图片相关信息
- transition(transition-property,transition-duration,transition-timing-function,transition-delay):只要是数值型以及颜色都可以参与过渡；
- 2D变换：transform(rotate/scale/skew/translate)
- 动画：@keyframes name{ from/0%{} ..%{}  to/100%{}};animation: name duration timing-function delay iteration-count direction fill-mode play-state;


## 选择器
1. css2选择器
- 标签,`*`,id,class
- 后代选择器` `
- 交集选择器`.`
- 并集选择器`,`
2. css3选择器
- 属性选择器：[key],[key="value"],[key|="value"](以value-开头或value属性值),[key~="value"](包含value单词的元素),[key^="value"],[key$="value"],[key\*="value"];`img[alt][src $="0.jpg"]`
- 子序列选择器：顺序：先按照n表达式计算匹配哪些子元素然后检查前面元素选择器是否匹配；:first-child(父元素下的第一个子元素)；:last-child(父元素下的最后一个子元素)；:nth-child(n)(n可以是表达式，n从1开始)；nth-last-child(n)(n从倒数第一个开始)；even,odd；直接n从1开始，表达式时an+m则n从0开始；
- 子类型选择器：顺序：先检查前面元素选择器的匹配再进行n的计算；:first-of-type(匹配同级元素中同种类型的第一个元素); :last-of-type; :nth-of-type(n); :hth-last-of-type(n);
- 关系节点选择器：`>`:子级选择器（只能选择儿子节点）；`+`：后面紧挨着的第一个亲兄弟；`～`：后面所有亲兄弟；



## 问题
### 塌陷问题
- 兄弟元素设置的下边距和上边距会合并以大的为准合并
- 后代元素设置的上边距会一直传递到body，并和父元素上边距合并，并以大的为准
    >> 解决：为父元素设置--padding或border或overflow:hidden.
### 百分比
- margin,padding使用百分比是相对于包含块的宽度
- widht,height使用百分比是相对于包含块的宽度,高度
- border-radiud使用百分比是宽度/高度对应的百分比计算
- background-size百分比是图片和盒子宽度/高度对应百分比计算
### 隐藏元素
- display:none---------不占位
- visibility:hidden;------占位
- opacity:0;------占位
### 居中
- text-align:center;padding/line-height;vertical-align:middle
- margin:0 auto;父元素设置padding;
- 用table 居中:display:table-cell;align:center;vertial-align:middle
- absolute:50%,self:50%
### margin
- 盒子没有设置宽度时，负值盒子宽度增加，正值盒子宽度减少；margin-left优先级高于margin-right(可以通过父元素的html标签align属性来更改优先级)
- 对浮动的影响：影响后面的元素，前面元素位置不受影响，设置margin超过其他浮动元素，则下一个浮动元素根据贴边原则进行移动---浮动贴边特性，当遇到了父元素边则贴到父元素边上。
