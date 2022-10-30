---
title: CSS学习笔记
catalog: true
index_img: /img/car_3.png
banner_img: /img/wave_bg1.jpg
date: 2022-10-03 08:58:57
subtitle:
tags: CSS
categories: Web
---



### 如何添加CSS ？

##### 三种使用CSS的方法：

- 外部CSS
- 内部CSS
- 行内CSS

> 行内样式拥有最高优先级，会覆盖外部和内部样式以及浏览器默认样式



### CSS单位

绝对长度：cm、mm、px、pc、pt、in

相对长度 ( 重点掌握)：em、rem、vw、vh、ex、ch、vmin、vmax、%   

| 单位 | 描述                                                         |
| :--- | ------------------------------------------------------------ |
| em   | 它是描述相对于应用在当前元素的字体尺寸。一般浏览器字体大小默认为16px，则2em==32px |
| rem  | rem作用于非根元素时，相对于根元素(如：html标签)字体大小；rem作用于根元素字体大小时，相对于其初始字体大小 |
| vw   | viewpoint width ,视窗宽度，1vw=视窗宽度的1%                  |
| vh   | viewpoint height，视窗高度，1vh=视窗高度的1%                 |
| vmin | vw和vh中较小的那一个                                         |
| vmax | vw和vh中较大的那一个                                         |
| ch   | 数字0的宽度                                                  |
| ex   | 依赖于英文字母x的高度                                        |
| %    |                                                              |

> 勿在属性值和单位之间添加空格（例如：`margin：20     px；`）。正确的写法是：`margin：20px；`   。



### CSS选择器

##### CSS组合器（根据它们之间的特定关系来选取元素）

- 后代选择器（空格）：`div p` : div元素的后代元素中所有p元素

- 子选择器（>）：`div>p` : div元素的子代元素中所有p元素
- 相邻兄弟选择器（+）：`div+p`：紧随div元素之后的p元素（“相邻”的意思是“紧随其后”）
- 通用兄弟选择器（~）：`div~p`：与div元素同级的所有p元素

##### CSS伪类（根据特定状态选取元素）

所有CSS伪类

| 选择器                                                       | 例子                  | 例子描述                                                     |
| :----------------------------------------------------------- | :-------------------- | :----------------------------------------------------------- |
| [:active](https://www.w3school.com.cn/cssref/selector_active.asp) | a:active              | 选择活动的链接。                                             |
| [:checked](https://www.w3school.com.cn/cssref/selector_checked.asp) | input:checked         | 选择每个被选中的 `<input>` 元素。                            |
| [:disabled](https://www.w3school.com.cn/cssref/selector_disabled.asp) | input:disabled        | 选择每个被禁用的 `<input>` 元素。                            |
| [:empty](https://www.w3school.com.cn/cssref/selector_empty.asp) | p:empty               | 选择没有子元素的每个 `<p>` 元素。                            |
| [:enabled](https://www.w3school.com.cn/cssref/selector_enabled.asp) | input:enabled         | 选择每个已启用的 `<input>` 元素。                            |
| [:first-child](https://www.w3school.com.cn/cssref/selector_first-child.asp) | p:first-child         | 选择作为其父的首个子元素的每个 `<p>` 元素。                  |
| [:first-of-type](https://www.w3school.com.cn/cssref/selector_first-of-type.asp) | p:first-of-type       | 选择作为其父的首个 `<p>` 元素的每个 `<p>` 元素。             |
| [:focus](https://www.w3school.com.cn/cssref/selector_focus.asp) | input:focus           | 选择获得焦点的 `<input>` 元素。                              |
| [:hover](https://www.w3school.com.cn/cssref/selector_hover.asp) | a:hover               | 选择鼠标悬停其上的链接。                                     |
| [:in-range](https://www.w3school.com.cn/cssref/selector_in-range.asp) | input:in-range        | 选择具有指定范围内的值的 `<input>` 元素。                    |
| [:invalid](https://www.w3school.com.cn/cssref/selector_invalid.asp) | input:invalid         | 选择所有具有无效值的 `<input>` 元素。                        |
| [:lang(*language*)](https://www.w3school.com.cn/cssref/selector_lang.asp) | p:lang(it)            | 选择每个 lang 属性值以 "it" 开头的 `<p>` 元素。              |
| [:last-child](https://www.w3school.com.cn/cssref/selector_last-child.asp) | p:last-child          | 选择作为其父的最后一个子元素的每个 `<p>` 元素。              |
| [:last-of-type](https://www.w3school.com.cn/cssref/selector_last-of-type.asp) | p:last-of-type        | 选择作为其父的最后一个 `<p>` 元素的每个 `<p>` 元素。         |
| [:link](https://www.w3school.com.cn/cssref/selector_link.asp) | a:link                | 选择所有未被访问的链接。                                     |
| [:not(*selector*)](https://www.w3school.com.cn/cssref/selector_not.asp) | :not(p)               | 选择每个非 `<p>` 元素的元素。                                |
| [:nth-child(*n*)](https://www.w3school.com.cn/cssref/selector_nth-child.asp) | p:nth-child(2)        | 选择作为其父的第二个子元素的每个 `<p>` 元素。                |
| [:nth-last-child(*n*)](https://www.w3school.com.cn/cssref/selector_nth-last-child.asp) | p:nth-last-child(2)   | 选择作为父的第二个子元素的每个`<p>`元素，从最后一个子元素计数。 |
| [:nth-last-of-type(*n*)](https://www.w3school.com.cn/cssref/selector_nth-last-of-type.asp) | p:nth-last-of-type(2) | 选择作为父的第二个`<p>`元素的每个`<p>`元素，从最后一个子元素计数 |
| [:nth-of-type(*n*)](https://www.w3school.com.cn/cssref/selector_nth-of-type.asp) | p:nth-of-type(2)      | 选择作为其父的第二个 `<p>` 元素的每个 `<p>` 元素。           |
| [:only-of-type](https://www.w3school.com.cn/cssref/selector_only-of-type.asp) | p:only-of-type        | 选择作为其父的唯一 `<p>` 元素的每个 `<p>` 元素。             |
| [:only-child](https://www.w3school.com.cn/cssref/selector_only-child.asp) | p:only-child          | 选择作为其父的唯一子元素的 `<p>` 元素。                      |
| [:optional](https://www.w3school.com.cn/cssref/selector_optional.asp) | input:optional        | 选择不带 "required" 属性的 `<input>` 元素。                  |
| [:out-of-range](https://www.w3school.com.cn/cssref/selector_out-of-range.asp) | input:out-of-range    | 选择值在指定范围之外的 `<input>` 元素。                      |
| [:read-only](https://www.w3school.com.cn/cssref/selector_read-only.asp) | input:read-only       | 选择指定了 "readonly" 属性的 `<input>` 元素。                |
| [:read-write](https://www.w3school.com.cn/cssref/selector_read-write.asp) | input:read-write      | 选择不带 "readonly" 属性的 `<input>` 元素。                  |
| [:required](https://www.w3school.com.cn/cssref/selector_required.asp) | input:required        | 选择指定了 "required" 属性的 `<input>` 元素。                |
| [:root](https://www.w3school.com.cn/cssref/selector_root.asp) | root                  | 选择元素的根元素。                                           |
| [:target](https://www.w3school.com.cn/cssref/selector_target.asp) | #news:target          | 选择当前活动的 #news 元素（单击包含该锚名称的 URL）。        |
| [:valid](https://www.w3school.com.cn/cssref/selector_valid.asp) | input:valid           | 选择所有具有有效值的 `<input>` 元素。                        |
| [:visited](https://www.w3school.com.cn/cssref/selector_visited.asp) | a:visited             | 选择所有已访问的链接。                                       |

所有CSS伪元素

| 选择器                                                       | 例子            | 例子描述                        |
| :----------------------------------------------------------- | :-------------- | :------------------------------ |
| [::after](https://www.w3school.com.cn/cssref/selector_after.asp) | p::after        | 在每个 `<p>` 元素之后插入内容。 |
| [::before](https://www.w3school.com.cn/cssref/selector_before.asp) | p::before       | 在每个 `<p>` 元素之前插入内容。 |
| [::first-letter](https://www.w3school.com.cn/cssref/selector_first-letter.asp) | p::first-letter | 选择每个 `<p>` 元素的首字母。   |
| [::first-line](https://www.w3school.com.cn/cssref/selector_first-line.asp) | p::first-line   | 选择每个 `<p>` 元素的首行。     |
| [::selection](https://www.w3school.com.cn/cssref/selector_selection.asp) | p::selection    | 选择用户选择的元素部分。        |



##### css属性选择器

| 选择器                                                       | 例子                | 例子描述                                                |
| :----------------------------------------------------------- | :------------------ | :------------------------------------------------------ |
| [[*attribute*\]](https://www.w3school.com.cn/cssref/selector_attribute.asp) | [target]            | 选择带有 target 属性的所有元素。                        |
| [[*attribute*=*value*\]](https://www.w3school.com.cn/cssref/selector_attribute_value.asp) | [target=_blank]     | 选择带有 target="_blank" 属性的所有元素。               |
| [[*attribute*~=*value*\]](https://www.w3school.com.cn/cssref/selector_attribute_value_contain.asp) | [title~=flower]     | 选择带有包含 "flower" 一词的 title 属性的所有元素。     |
| [[*attribute*\|=*value*\]](https://www.w3school.com.cn/cssref/selector_attribute_value_start.asp) | [lang\|=en]         | 选择带有以 "en" 开头的 lang 属性的所有元素。            |
| [[*attribute*^=*value*\]](https://www.w3school.com.cn/cssref/selector_attr_begin.asp) | a[href^="https"]    | 选择其 href 属性值以 "https" 开头的每个 <a> 元素。      |
| [[*attribute*$=*value*\]](https://www.w3school.com.cn/cssref/selector_attr_end.asp) | a[href$=".pdf"]     | 选择其 href 属性值以 ".pdf" 结尾的每个 <a> 元素。       |
| [[*attribute**=*value*\]](https://www.w3school.com.cn/cssref/selector_attr_contain.asp) | a[href*="w3school"] | 选择其 href 属性值包含子串 "w3school" 的每个 <a> 元素。 |



#### css颜色

主要有RGB颜色、HEX颜色、HSL颜色

##### RGB值

rgb(red,green,blue)

##### RGBA值

rgba(red,green,blue,alpha)

> RGB的扩展，指定了颜色的不透明度，alpha参数是介于0.0（完全透明）和1.0（完全不透明）之间的数字

##### HEX值

#rrggbb

> 使用十六进制值指定颜色,其中rr（红色）、gg（绿色）和bb（蓝色）是介于00和ff之间的十六进制值，例如：#ffffff（白色）

##### HSL值

hsl(hue,saturation,lightness)

> 色相（hue）是色轮上从0~360的度数。0是红色，120是绿色，240是蓝色。
>
> 饱和度（saturation）是一个百分比值，0%是灰色阴影，而100%是全色。
>
> 亮度（lightness）也是百分比，0%是黑色，50%是既不明也不暗，100%是白色。
>
> 例如：hsl(147,50%,47%) 浅绿色

##### HSLA值

hsla(hue,saturation,lightness,alpha)

> HSL的扩展，指定了颜色的不透明度，alpha参数是介于0.0（完全透明）和1.0（完全不透明）之间的数字



##### [在线调色板](https://www.sojson.com/web/panel.html)





#### 透明度：

**opacity**  : 会应用到子元素上

**rgba** : 不会应用到子元素上





#### css背景

背景图：

background-image: url("paper.jpg")

背景重复：

background-repeat: value

value=repeat-x：仅水平方向重复

value=repeat-y：仅垂直方向重复

value=no-repeat：图像仅显示一次

背景图像位置(示例)：

background-position：right  top；（背景图位于右上方）

背景附着：

background-attachment：value

value=fixed：背景图固定，不随页面其余内容滚动

value=scroll：背景图随页面其他内容滚动

背景简写：

例：`background: #ffffff url("tree.png") no-repeat right top;`

简写顺序：

- background-color
- background-image
- background-repeat
- background-attachment
- background-position



#### css文本

##### 文本颜色

color：value;

##### 文本对齐

text-align：value；

value=center；（居中对齐）

value=left；（左对齐）

value=right；（右对齐）

value=justify；（拉伸每一行，且左右边距是直的）

##### 垂直对齐

vertical-align：value；

value=top; (上对齐)

value=middle;(居中对齐)

value=bottom;(下对齐)

##### 文本方向  

direction：value

value=ltr；（默认，从左向右）

value=rtl；（从右向左）

value=inherit；（从父元素继承）

##### 文字装饰

text-decoration：value;

value=none；（默认，无装饰）

value=underline；（定义文本下的一条线）

value=overline；（定义文本上的一条线）

value=line-through；（定义穿过文本的一条线）

##### 文本转换

text-transform：value；

value=uppercase；（大写）

value=lowercase；（小写）

value=capitalize；（每个单词首字母大写）

##### 文字间距

文字缩进：text-indent  (指定文本第一行缩进)

字母间距：letter-spacing  (指定文本中字符之间的间距)

行高：line-height (指定行之间的间距)

字间距：word-spacing (指定文本中单词之间的间距)

空白：white-space（指定元素内部空白的处理方式）

##### [文字阴影](https://www.w3school.com.cn/css/css_text_shadow.asp)

text-shadow



#### CSS边框

CSS border属性可以设置边框的样式、宽度和颜色。

边框样式  `border-style`   属性有以下值：

- `dotted` - 定义点线边框
- `dashed` - 定义虚线边框
- `solid` - 定义实线边框
- `double` - 定义双边框
- `groove` - 定义 3D 坡口边框。效果取决于 border-color 值
- `ridge` - 定义 3D 脊线边框。效果取决于 border-color 值
- `inset` - 定义 3D inset 边框。效果取决于 border-color 值
- `outset` - 定义 3D outset 边框。效果取决于 border-color 值
- `none` - 定义无边框
- `hidden` - 定义隐藏边框

边框宽度  `border-width`  

边框颜色  `border-color`  

可以为不同的边设置不同的边框，如：

```css
div {
  border-top-style: dotted;
  border-right-style: solid;
  border-bottom-style: dotted;
  border-left-style: solid;
}
```

简写边框属性（width  style  color)

```css
p {
  border: 5px solid red;
}
```

圆角边框  `border-radius`  



#### CSS 外边距  `margin`  

> 可以是负值

外边距合并：当两个垂直外边距相遇时，它们将形成一个外边距。合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者。

> - margin: 25px 50px 75px 100px;
>
> 上外边距25px，右外边距50px，下外边距75px，左外边距100px
>
> - margin：25px  50px  75px；
>
> 上外边距25px，左右外边距50px，下外边距75px
>
> - margin：25px  50px；
>
> 上下外边距25px，左右外边距50px



#### CSS内边距  `padding`

> 不可为负值

> - padding : 25px  50px  75px  100px;
>
> 上内边距25px，右内边距50px，下内边距75px，左内边距100px
>
> - padding：25px  50px  75px；
>
> 上内边距25px，左右内边距50px，下内边距75px
>
> - padding：25px  50px；
>
> 上下内边距25px，左右内边距50px



#### [CSS轮廓](https://www.w3school.com.cn/css/css_outline.asp)

CSS轮廓是在元素周围绘制的一条线，在边框之外，以凸显元素。轮廓不计入元素尺寸中，元素的总高度和总宽度不受轮廓宽度的影响。

CSS有如下轮廓属性：

- `outline-style`   轮廓样式（可选择如下值）
  - `dotted` - 定义点状的轮廓。
  - `dashed` - 定义虚线的轮廓。
  - `solid` - 定义实线的轮廓。
  - `double` - 定义双线的轮廓。
  - `groove` - 定义 3D 凹槽轮廓。
  - `ridge` - 定义 3D 凸槽轮廓。
  - `inset` - 定义 3D 凹边轮廓。
  - `outset` - 定义 3D 凸边轮廓。
  - `none` - 定义无轮廓。
  - `hidden` - 定义隐藏的轮廓。	
- `outline-color`   轮廓颜色
- `outline-width`   轮廓宽度
- `outline-offset`   轮廓偏移
- `outline`   轮廓简写 （可包含如下值）
  - `outline-width`
  - `outline-style`（必需）
  - `outline-color`



#### CSS定位

##### position属性(有如下值)

- static (默认值)
- relative
- fixed

> 设置此属性值的元素是相对于视口定位的，即使滚动页面，它也始终位于同一位置。top、right、bottom和left属性用于定位此元素。

- absolute

> 需与 `position:relative;`  的祖先元素组合使用

- sticky

> 粘性定位，粘性元素根据滚动位置在相对（relative）和固定（fixed）之间切换。它会被相对定位，知道在视口中遇到给定的偏移位置为止，然后将其“粘贴”在适当的位置。



#### CSS溢出

##### overflow  overflow-x   overflow-y

> 仅适用于具有指定高度的块元素

- `visible` - 默认。溢出没有被剪裁。内容在元素框外渲染
- `hidden` - 溢出被剪裁，其余内容将不可见
- `scroll` - 溢出被剪裁，同时添加滚动条以查看其余内容
- `auto` - 与 `scroll` 类似，但仅在必要时添加滚动条



#### Box Sizing

> 定义元素宽度和高度的计算方式，它们是否应包含内边距和边框。

`box-sizing：border-box;`   元素宽度和高度包含内边距和边框



#### [CSS水平与垂直对齐、居中](https://www.w3school.com.cn/css/css_align.asp)



#### CSS边框图像

`border-image`   属性允许指定图像为边框，而不是包围普通边框。



#### CSS多重背景

可以通过  `background-image`  属性为一个元素添加多幅背景图像。不同的背景图像用逗号隔开，并且图像会彼此重叠，其中第一幅图像最靠近观看者。

> 相关属性：background-size、background-repeat、background-origin、background-clip





#### [CSS阴影效果](https://www.w3school.com.cn/css/css3_shadows.asp)

- `text-shadow`
- `box-shadow`



#### [CSS文本效果](https://www.w3school.com.cn/css/css3_text_effects.asp)

CSS文本溢出、整字换行、换行规则以及书写模式

- `text-overflow`
- `word-wrap`
- `word-break`
- `writing-mode`



#### [CSS  2D 转换](https://www.w3school.com.cn/css/css3_2dtransforms.asp)

##### transform 属性

- `translate()`    将其从当前位置移动元素（根据为X轴和Y轴指定的参数）
- `rotate()`    根据给定的角度顺时针或逆时针旋转元素
- `scaleX()`    增加或减少元素的宽度
- `scaleY()`    增加或减少元素的高度
- `scale()`    根据给定的宽度和高度参数增加或减少元素的大小
- `skewX()`   使元素沿X轴倾斜给定角度
- `skewY()`   使元素沿Y轴倾斜给定角度
- `skew()`   使元素沿X轴和Y轴倾斜给定角度
- `matrix()`   此方法把所有的2D变换方法组合为一个，可接受六个参数，使用这些参数可以实现旋转、缩放、移动和倾斜元素，参数如下：matrix( scaleX( ), skewY( ), skewX( ), scaleY( ), tranlateX( ), translateY( ) )



#### [CSS  3D 转换](https://www.w3school.com.cn/css/css3_3dtransforms.asp)

##### transform属性

- `rotateX()`    将元素绕其X轴旋转给定角度
- `rotateY()`    将元素绕其Y轴旋转给定角度
- `rotateZ()`    将元素绕其Z轴旋转给定角度



#### [CSS过渡](https://www.w3school.com.cn/css/css3_transitions.asp)

- ##### transition  

> 简写属性，用于将四个过渡属性设置为单一属性
>
> 顺序：property  duration   timing-function   delay
>
> 例如：`transition: width 2s linear 1s;`

- ##### transition-delay  

> 规定过渡效果的延迟
>
> 例如：`transition-delay: 1s;`

- ##### transition-duration

> 规定过渡效果要持续多久
>
> 例如：`transition-duration: 2s;`

- ##### transition-property

> 规定过渡效果所针对的CSS属性的名称
>
> 例如：`transition-property: width;`

- ##### transition-timing-function

> 规定过渡效果的速度曲线
>
> 例如：`transition-timing-function: linear;`
>
> 可接受如下值：
>
> - `ease` - 规定过渡效果，先缓慢地开始，然后加速，然后缓慢地结束（默认）
> - `linear` - 规定从开始到结束具有相同速度的过渡效果
> - `ease-in` -规定缓慢开始的过渡效果
> - `ease-out` - 规定缓慢结束的过渡效果
> - `ease-in-out` - 规定开始和结束较慢的过渡效果
> - `cubic-bezier(n,n,n,n)` - 允许您在三次贝塞尔函数中定义自己的值



#### 

#### [CSS 动画](https://www.w3school.com.cn/css/css3_animations.asp)

动画使元素逐渐从一种样式变为另一种样式，可以随意更改任意数量的CSS属性。使用CSS动画时需先为动画指定一些关键帧，关键帧包含元素在特定时间所拥有的样式。



- ##### @keyframes

> 在`@keyframes`规则中指定CSS样式后，动画将在特定时间逐渐从当前样式更改为新样式。
>
> 要使动画生效，必须将动画绑定到某个元素
>
> 代码示例：
>
> ```css
> /* 动画代码 */
> @keyframes example {
>   from {background-color: red;}
>   to {background-color: yellow;}
> }
> /* 向此元素应用动画效果 */
> div {
>   width: 100px;
>   height: 100px;
>   background-color: red;
>   animation-name: example;
>   animation-duration: 4s;
> }
> ```

> 在例子中，通过使用关键字“from”和“to"（代表0%（开始）和100%（完成）），设置样式何时改变，也可使用百分比值，通过使用百分比，可以根据需要添加任意多个样式更改。

> ```css
> /* 动画代码 */
> @keyframes example {
>   0%   {background-color:red; left:0px; top:0px;}
>   25%  {background-color:yellow; left:200px; top:0px;}
>   50%  {background-color:blue; left:200px; top:200px;}
>   75%  {background-color:green; left:0px; top:200px;}
>   100% {background-color:red; left:0px; top:0px;}
> }
> 
> /* 应用动画的元素 */
> div {
>   width: 100px;
>   height: 100px;
>   position: relative;
>   background-color: red;
>   animation-name: example;
>   animation-duration: 4s;
> }
> ```

- ##### animation-name

  > 规定@keyframes动画的名称

- ##### animation-duration  

  > 定义需要多长时间才能完成动画。

- ##### animation-delay

  > 规定动画开始的延迟时间。

- ##### animation-iteration-count

  > 设置动画应运行多少次，使用值”infinite“将会使动画永远持续下去。

- ##### animation-direction

  > 反向或交替运行动画，该属性指定向前播放、向后播放还是交替播放动画
  >
  > 有以下值可供选择：
  >
  > - `normal` - 动画正常播放（向前）。默认值
  > - `reverse` - 动画以反方向播放（向后）
  > - `alternate` - 动画先向前播放，然后向后
  > - `alternate-reverse` - 动画先向后播放，然后向前

- ##### animation-timing-function

  > 指定动画的速度曲线，有以下值可供选择：
  >
  > - `ease` - 指定从慢速开始，然后加快，然后缓慢结束的动画（默认）
  > - `linear` - 规定从开始到结束的速度相同的动画
  > - `ease-in` - 规定慢速开始的动画
  > - `ease-out` - 规定慢速结束的动画
  > - `ease-in-out` - 指定开始和结束较慢的动画
  > - `cubic-bezier(*n*,*n*,*n*,*n*)` - 运行您在三次贝塞尔函数中定义自己的值

- ##### animation-fill-mode

  > 指定动画的填充模式，有以下值可供选择：
  >
  > - `none` - 默认值。动画在执行之前或之后不会对元素应用任何样式。
  > - `forwards` - 元素将保留由最后一个关键帧设置的样式值（依赖 animation-direction 和 animation-iteration-count）。
  > - `backwards` - 元素将获取由第一个关键帧设置的样式值（取决于 animation-direction），并在动画延迟期间保留该值。
  > - `both` - 动画会同时遵循向前和向后的规则，从而在两个方向上扩展动画属性

- ##### animation

  > 动画简写属性

  > ```css
  > div {
  >   animation: example 5s linear 2s infinite alternate;
  > }
  > /*等同于下面的样式*/
  > ```
  >
  > ```css
  > div {
  >   animation-name: example;
  >   animation-duration: 5s;
  >   animation-timing-function: linear;
  >   animation-delay: 2s;
  >   animation-iteration-count: infinite;
  >   animation-direction: alternate;
  > }
  > ```





#### CSS   object-fit 属性

该属性用于规定应如何调整`<img>`  或  `<video>`  的大小来适应其容器。

有如下值可供选择：

- `fill` - 默认值。调整替换后的内容大小，以填充元素的内容框。如有必要，将拉伸或挤压物体以适应该对象。
- `contain` - 缩放替换后的内容以保持其纵横比，同时将其放入元素的内容框。
- `cover` - 调整替换内容的大小，以在填充元素的整个内容框时保持其长宽比。该对象将被裁剪以适应。
- `none` - 不对替换的内容调整大小。
- `scale-down` - 调整内容大小就像没有指定内容或包含内容一样（将导致较小的具体对象尺寸）



#### [CSS  多列](https://www.w3school.com.cn/css/css3_multiple_columns.asp)

- ##### column-count

  > 规定元素应被划分的列数
  >
  > `column-count: 3;`

- ##### column-gap

  > 规定列之间的间隙
  >
  > `column-gap: 40px;`

- ##### column-rule-style

  > 规定列之间的规则样式
  >
  > `column-rule-style: solid;`

- ##### column-rule-width

  > 规定列之间的规则宽度
  >
  > `column-rule-width: 1px;`

- ##### column-rule-color

  > 规定列之间的规则的颜色
  >
  > `column-rule-color: lightblue;`

- ##### column-rule

  > 设置列之间的规则的宽度、样式和颜色，简写属性
  >
  > `column-rule: 1px solid lightblue;`

- ##### column-span

  > 规定元素应跨多少列
  >
  > 可供选择的值：1 、 all

- ##### column-width

  > 为列指定建议的最佳宽度（？跟column-count同时使用会产生冲突）



#### CSS  用户界面

- ##### resize

  > 规定元素是否应（以及如何）被用户调整大小
  >
  > 在许多浏览器中`<textarea>`  默认可调整大小
  >
  > ```css
  > div {
  >   resize: horizontal;
  >   overflow: auto;
  > }/*只允许用户调整元素的宽度*/
  > 
  > div {
  >   resize: vertical;
  >   overflow: auto;
  > }/*只允许用户调整高度*/
  > 
  > div {
  >   resize: both;
  >   overflow: auto;
  > }/*允许用户调整宽度和高度*/
  > ```

- ##### outline-offset

  > CSS 轮廓偏移，此属性在轮廓与元素的边缘边框之间添加空间。



#### CSS  变量

var()函数用于插入CSS变量的值，CSS变量可通过 JavaScript 修改

> CSS 变量可以有全局或局部作用域。全局变量可以在整个文档中进行访问/使用，而局部变量只能在声明它的选择器内部使用。
>
> 如需创建具有全局作用域的变量，在  :root 选择器中声明它。:root  选择器匹配文档的根元素。
>
> 如需创建具有局部作用域的变量，在将要使用它的选择器中声明它。

代码示例：

```css
:root {
  --blue: #1e90ff;
  --white: #ffffff;
}

body { background-color: var(--blue); }

h2 { border-bottom: 2px solid var(--blue); }

.container {
  color: var(--blue);
  background-color: var(--white);
  padding: 15px;
}

button {
  background-color: var(--white);
  color: var(--blue);
  border: 1px solid var(--blue);
  padding: 5px;
}
```

> 使用var()，可以使代码更易于阅读，使修改颜色值更加容易。

##### 覆盖变量

若局部变量的名称与全局变量的名称一样时，全局变量将会被覆盖，使用局部变量的值。





#### [CSS  Flexbox](https://www.w3school.com.cn/css/css3_flexbox.asp)

通过将display属性设置为flex，flex容器将可伸缩。

- ##### flex-direction

> 定义容器在哪个方向堆叠flex项目

| 值             | 排列方向 |
| -------------- | -------- |
| column         | 从上到下 |
| column-reverse | 从下到上 |
| row            | 从左到右 |
| row-reverse    | 从右到左 |

- ##### flex-wrap

> 规定flex项目是否应该换行
>
> 可供选择的值：wrap   nowrap   wrap-reverse

- ##### flex-flow

> flex-flow 属性是用于同时设置 flex-direction 和 flex-wrap 属性的简写属性。

- ##### justify-content

> 用于对齐flex项目
>
> - center：中心对齐
> - flex-start：在容器的开头对齐（默认值）
> - flex-end：在容器的末端对齐
> - space-around：显示行之前、之间和之后带有空格的flex项目
> - space-between：显示行之间带有空格的flex项目

- ##### align-items

> 用于垂直对齐flex项目
>
> - center：将flex项目在容器中间对齐
> - flex-start：将flex项目在容器顶部对齐
> - flex-end：将弹性项目在容器底部对齐
> - stretch：拉伸flex项目以填充容器（默认）
> - baseline：使项目基线对齐（项目的第一行文字的基线对齐）

- ##### align-content

> 用于对齐弹性线
>
> - space-between：显示的弹性线之间有相等的间距
> - space-around：显示弹性线在其之前、之间和之后带有空格
> - stretch：拉伸弹性线以占据剩余空间（默认）
> - center：在容器中间显示弹性线
> - flex-start：在容器的开头显示弹性线
> - flex-end：在容器的末尾显示弹性线

flex容器的直接子元素会自动成为弹性（flex）项目

弹性项目的属性

- ##### order

> order属性规定flex项目的顺序

- ##### flex-grow

> 规定某个flex项目相对于其余flex项目将增长多少

- ##### flex-shrink

> 规定某个flex项目相对于其余flex项目将收缩多少

- ##### flex-basis

> 规定弹性项目的初始长度

- ##### flex

> flex 属性是 flex-grow、flex-shrink 和 flex-basis 属性的简写属性。

- ##### align-self

> 规定弹性容器所选项目的对齐方式，此属性将覆盖容器的align-items属性所设置的默认对齐方式







#### [CSS 媒体查询](https://www.w3school.com.cn/cssref/pr_mediaquery.asp)

@media 规则在媒体查询中用于为不同的媒体类型/设备应用不同的样式。

媒体查询可用于检查许多事情，诸如：

- 视口的宽度和高度
- 设备的宽度和高度
- 方向（手机或平板电脑处于横屏还是竖屏模式？）
- 分辨率

使用媒体查询是一种流行的技术，用于向台式机、笔记本电脑、平板电脑和手机提供定制的样式表（响应式网页设计）。







## Q&A

#### box-sizing属性值的作用

用来控制元素的盒子模型的解析模式，默认值为content-box

- `context-box`：设置元素的height/width属性指的是content部分的高/宽

- `border-box`：设置元素的height/width属性指的是border+padding+content部分的高/宽

  

#### absolute绝对定位

CSS  position属性用于指定一个元素在文档中的定位的方式，absolute的元素会被移出正常文档流，通过指定元素相对于最近的非static定位祖先元素进行定位，确定元素位置。绝对定位的元素可以设置外边距，且不会与其他边距合并。



#### 行内元素和块级元素的区别

- 通常情况下行内元素不会另起一行，块级元素会另起一行

- 块级元素可以设置宽高，即width和height属性值，但块级元素即便设置了宽度，依然是独占一行的。而行内元素设置height,width无效。

- 块级元素可以设置内外边距，而行内元素只能设置水平方向的padding-left/right、margin-left/right，竖直方向的padding-top/bottom,margin-top/bottom属性值不会产生边距效果

- 块级元素可以包含行内元素和块级元素，行内元素不能包含块级元素

  

#### 检测浏览器所支持的最小字体大小

使用JS设置DOM的字体为某一个值，然后取出来，若设置成功则说明支持。



#### CSS中的”`flex：1;`”

flex是flex-grow，flex-shrink和flex-basis的简写。

除了auto和none这两个快捷值外，还有以下设置方式：

- 当flex取值为一个非负数字，则该数字为flex-grow的值，flex-shrink取1，flex-basis取0%
- 当flex取值为0时，对应的三个值分别为0  1  0%



#### CSS不支持父选择器

浏览器解析HTML文档，时从前往后，由里及外的。我们时常会看到页面先出现头部然后主题内容再出现的加载情况。如果CSS支持父选择器，那么就要等页面所有子元素加载完毕才能渲染HTML文档，父选择器即后代元素会影响祖先元素，后代元素还没处理完时无法影响祖先元素。因此网页的渲染速度会大大减慢，浏览器会出现长时间的白板。



####  隐藏页面元素的方式

- `display：none;`  元素不可见，不占据空间，无法响应点击事件
- `visibility：hidden;`  元素不可见，占据页面空间，无法响应点击事件
- `opacity：0;`   改变元素透明度，元素不可见，占据页面空间，可以响应点击事件
- 将元素的margin，border，padding，height和width等值设置为0，若元素内有子元素或者内容，还应设置其`overflow：hidden; `来隐藏子元素,元素不可见，不占据空间，无法响应点击事件
- `position：absolute;`   将元素移出可视区域元素不可见，不影响页面布局
- clip-path   通过裁剪的形式，元素不可见，占据页面空间，无法响应点击事件



#### 前端项目初始化CSS样式

由于浏览器的兼容问题，不同浏览器对标签的默认值是不一样的，如果没有对浏览器的CSS初始化，会造成相同页面在不同浏览器的显示存在差异。



#### display:none 和visibility:hidden 在性能上的区别

使用 visibility:hidden 比 display:none 要好，后者在切换显示时，页面会产生回流，而前者不会



#### 硬件加速

- 将浏览器的渲染过程交给GPU处理，而不是使用自带的比较慢的渲染器。这样可以使得animation和transition更加顺畅。

- 在浏览器中用CSS开启硬件加速，使GPU发挥功能，从而可以提升性能。

  

#### ::before和:after中双冒号和单冒号的区别

- 单冒号(:)用于CSS3伪类，匹配元素的一些特殊状态，如hover、link等
- 双冒号(::)用于CSS3伪元素（伪元素由双冒号和伪元素名称组成），伪元素一般匹配的是特殊位置，如after,before等



#### CSS样式匹配规则

从右向左！



#### CSS优化、提高性能的方法

- 避免后代选择符
- 避免链式选择符
- 使用紧凑的语法
- 避免不必要的命名空间
- 避免不必要的重复
- 避免！important，可以选择其他选择器
- 尽可能精简规则，合并不同类里的重复规则



#### style标签写在body前面与后面的区别

页面加载自上而下，style标签在前则先加载样式；若写在body标签后由于浏览器以逐行的方式对HTML文档进行解析，当解析到写在尾部的样式表会导致浏览器停止之前的渲染，等待加载且解析样式表完成之后重新渲染，在某些浏览器下会因样式失效导致页面闪烁



#### 元素竖向的百分比

当按百分比设定一个元素的宽度时，它是相对于父容器的宽度计算的，但是，对于一些表示竖向距离的属性，如padding-top、padding-bottom、margin-top、margin-bottom等，按百分比设定时，依据的也是父容器的宽度，而不是高度。



#### transition和animation的区别

- `transition` 是过渡属性，强调过渡，它的实现需要触发一个事件（比如鼠标移动上去，焦点，点击等）才执行动画
- `animation `是动画属性，它的实现不需要触发事件，设定好时间之后可以自己执行，且可以循环一个动画



#### 盒子模型

由四个部分组成：content、padding、border、margin



#### 脱离文档流的方法

float：使用float脱离文档流时，其他盒子会无视这个元素，但其他盒子内的文本依然会为这个元素让出位置，环绕在该元素的周围

absolute：绝对定位，是相对于该元素的父类元素进行定位的，且这个父类元素的position必须不为static

fixed：固定定位，完全脱离文档流，相对于浏览器窗口进行定位。（相对于浏览器窗口就是相对于html）



#### CSSOM树和DOM树的解析

浏览器会下载HTML解析页面生成DOM树，遇到CSS标签就开始解析CSS，这个过程不会阻塞，但是如果遇到了JS脚本，此时假如CSSOM还没有构建完，需等待CSSOM构建完，再去执行JS脚本，然后再执行DOM解析，此时会阻塞。



#### CSS  Sprites

一种网页图片应用处理方式，就是把网页中的一些背景图片整合到一张图片文件中，再利用CSS的`background-image` 、`background-repeat` 、`background-position`  的组合进行背景定位。

优点：

- 减少网页的http请求，提高性能
- 减少图片的字节：多张图片合成一张图片的字节小于多张图片的字节总和
- 减少了命名困扰：只需要对一张集合的图片命名，不需要对每一个小元素进行命名提高制作效率

缺点：

- 图片合成比较麻烦
- 背景设置时，需要得到每一个背景单元的精确位置
- 维护困难



#### 手写动画最小的时间间隔

大多数显示器默认频率是60Hz，即1秒刷新60次，所以理论上最小的时间间隔为1/60*1000ms=16.7ms



#### 两个inline-block节点间出现间隔

元素被当成行内元素排版时，元素之间的空白符（空格、回车换行等）都会被浏览器处理，原来HTML代码中的回车换行被转成一个空白符，在字体不为0的情况下，空白符占据一定宽度，所以inline-block的元素之间出现间隙。这些元素之间的间距会随着字体的大小而变化，当行内元素font-size：16px 时，间距为8px。

解决方法：

- 移除空格
- 使用margin负值
- 使用font-size：0
- 使用letter-spacing
- 使用word-spacing



#### Sass、Less

CSS预处理器，是CSS上的一种抽象层。Less是一种动态样式语言，将CSS赋予了动态语言的特性，如变量、运算、函数，Less既可以在客户端上运行，也可以在服务端运行（借助Node.js）



#### CSS动画  VS  JS实现动画

CSS动画

优点：

- 浏览器可以对动画进行优化
- 代码相对简单
- 对于帧速表现不好的低版本浏览器，CSS3可以做到自然降级，而JS需要撰写额外代码

缺点：

- 运行过程中控制较弱，无法附加事件绑定回调函数
- 代码冗长，实现复杂动画时代码量笨重

JS动画

优点：

- 控制能力很强，可以在动画播放过程中对动画进行控制：开始、暂停、回放、中止、取消都可以做到
- 动画效果比CSS3动画丰富，有些动画效果，如曲线运动、冲击闪烁、视差滚动效果，只有JS动画才能完成
- CSS3有兼容性问题，而JS大多时候没有兼容性问题

缺点：

- 代码复杂度高于CSS动画
- JavaScript在浏览器的主线程中运行，而主线程中还有其他需要运行的JavaScript脚本、样式计算、布局、绘制任务等，对其干扰导致线程可能出现阻塞，从而造成丢帧的情况



#### z-index失效

- 父元素position为relative时，子元素的z-index失效
- 该元素没有设置position为非static属性
- 元素在设置z-index的同时还设置了float浮动



#### 浏览器渲染的流程

1、HTML解析文件，生成DOM Tree，解析CSS文件生成CSSOM Tree

2、将DOM Tree 和CSSOM Tree结合，生成Render Tree（渲染树）

3、根据Render  Tree渲染绘制，将像素渲染到屏幕上



#### 设置overflow：scroll 不能平滑滚动

加上代码：

`-webkit-overflow-scrolling：touch;`



#### 无依赖绝对定位

没有设置left/top/right/bottom属性值的绝对定位称为”无依赖绝对定位“。无依赖绝对定位其定位的位置和没有设置position：absolute 时候的位置相关。



#### 层叠准则

谁大谁上：z-index值大的覆盖值z-index小的

后来居上：当层叠水平一致，在DOM流中处于后面的元素会覆盖前面的元素。



#### text-indent

该属性规定文本块中首行文本的缩进。





















