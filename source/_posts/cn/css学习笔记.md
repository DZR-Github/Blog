---
title: CSS学习笔记
catalog: true
header-img: /img/scenery/wave_bg1.jpg
date: 2022-10-03 08:58:57
subtitle:
tags: CSS
categories: Web
---



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



### CSS选择器

##### CSS组合器（根据它们之间的特定关系来选取元素）

- 后代选择器（空格）：`div p` : div元素的后代元素中所有p元素

- 子选择器（>）：`div>p` : div元素的子代元素中所有p元素
- 相邻兄弟选择器（+）：`div+p`：紧随div元素之后的p元素（“相邻”的意思是“紧随其后”）
- 通用兄弟选择器（~）：`div~p：与div元素同级的所有p元素

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

![](https://raw.githubusercontent.com/DZR-Github/IMGS/main/202206022103513.png)

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

##### 文字阴影

text-shadow

































