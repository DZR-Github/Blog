---
title: CSS学习笔记
catalog: true
header-img: /img/scenery/wave_bg1.jpg
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











