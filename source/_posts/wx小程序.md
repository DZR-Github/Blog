---
title: wx小程序
catalog: true
date: 2022-09-20 22:39:45
subtitle: 
index_img: /img/star_2.jpg
banner_img: /img/City_1.jpg
tags: 微信小程序开发
categories: 小程序
---



## 小程序配置文件

一个小程序应用程序会包含最基本的两种配置文件。一种是全局的`app.json`和页面自己的`page.json`

#### 全局配置`app.json`

`app.json`是当前小程序的全局配置，包括了小程序的所有页面路径、页面表现、网络超时时间、底部tab等。普通快速启动项目里边的`app.json`配置

```json
{
 "pages":[
  "pages/index/index",
  "pages/logs/logs"
],
 "window":{
  "backgroundTextStyle":"light",
  "navigationBarBackgroundColor": "#fff",
  "navigationBarTitleText": "WeChat",
  "navigationBarTextStyle":"black"
}
}
```

字段的含义

1、`pages`字段：用于描述当前小程序所有页面路径，这是为了让微信客户端知道当前你的小程序页面定义在哪个目录。

2、`window`字段：定义小程序所有页面的顶部背景颜色，文字颜色定义等。

3、完整的配置信息参考[app.json配置](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html)



#### tabbar



#### [页面配置page.json](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/page.html)

这里的`page.json`其实用来表示页面目录下的`page.json`这类和小程序页面相关的配置。

开发者可以独立定义每个页面的一些属性，如顶部颜色、是否允许下拉刷新等等。

页面的配置只能设置`app.json`中部分`window`配置项的内容，页面中配置项会覆盖`app.json`中的`window`中相同的配置项。

| 属性                         | 类型     | 默认值  | 描述                                                         |
| ---------------------------- | -------- | ------- | ------------------------------------------------------------ |
| navigationBarBackgroundColor | HexColor | #000000 | 导航栏背景颜色，如 `#000000`                                 |
| navigationBarTextStyle       | string   | white   | 导航栏标题颜色，仅支持 `black` / `white`                     |
| navigationBarTitleText       | string   |         | 导航栏标题文字内容                                           |
| navigationStyle              | string   | default | 导航栏样式，仅支持以下值： `default` 默认样式  `custom` 自定义导航栏，只保留右上角胶囊按钮。 |
| homeButton                   | boolean  | false   | 在非首页、非页面栈最底层页面或非 tabbar 内页面中的导航栏展示 home 键 |





## 模板语法

### 数据绑定

1、普通写法

`<view> {{ message }} </view>`

```js
Page({
 data: {
  message: 'Hello MINA!'
}
})
```

2、bool类型

`<checkbox checked="{{false}}"> </checkbox>`

### 运算

1、三元运算

`<view hidden="{{flag ? true : false}}"> Hidden </view>`

2、算数运算

`<view> {{a + b}} + {{c}} + d </view>`

```js
Page({
 data: {
  a: 1,
  b: 2,
  c: 3
}
})
```

3、逻辑判断

`<view wx:if="{{length > 5}}"> </view>`

4、字符串运算

`<view>{{"hello" + name}}</view>`

```js
Page({
 data:{
  name: 'MINA'
}
})
```

> 花括号和引号之间不能有空格，若有，则会被解析为字符串
>

### 列表渲染

##### 1、wx:for

项的变量名默认为`item` `wx:for-item` 可以指定数组当前元素的变量名

下标变量名默认为`index` `wx:for-index` 可以指定数组当前下标的变量名

`wx:key` 用来提高数组渲染的性能

`wx:key` 绑定的值有如下选择

- `string` 类型，表示循环项中的唯一属性  如

```
list:[{id:0,name:"炒饭"},{id:1,name:"炒面"}]
wx:key="id"
```

- 保留字`*this` ，它的意思是`item` 本身。*this 代表的必须是唯一的字符串和数组。

```
list:[1,2,3,4,5]
wx:key="*this"
```

代码：

```html
<view wx:for="{{array}}" wx:key="id">
{{index}}: {{item.message}}
</view>
```

```js
Page({
 data: {
  array: [{
   id:0,
   message: 'foo',
 }, {
   id:1,
   message: 'bar'
 }]
}
})
```

##### 2、block

渲染一个包含多节点的结构块block最终不会变成真正的dom元素

```html
<block wx:for="{{[1, 2, 3]}}" wx:key="*this" >
 <view> {{index}}: </view>
 <view> {{item}} </view>
</block>
```

### 条件渲染

##### 1、wx:if

在框架中，使用`wx:if="{{condition}}"` 来判断是否需要渲染该代码块：

```html
 <view wx:if="{{false}}">1</view>
 <view wx:elif="{{true}}">2</view>
 <view wx:else>3</view>
```

##### 2、hidden

`<view hidden="{{condition}}"> True </view>`

> 类似`wx:if`

频繁切换  用`hidden`    

不常使用  用`wx:if`





## 小程序事件的绑定

小程序中绑定事件，通过bind关键字来实现。如`bindtap`   `bindinput`   `bindchange`  等不同的组件支持不同的事件，具体看组件的说明即可。

#### 1、wxml

`<input bindinput="handleInput" />`

#### 2、page

```js
Page({
 // 绑定的事件
 handleInput: function(e) {
  console.log(e);
  console.log("值被改变了");
}
})
```

#### 3、特别注意

1、绑定事件时不能带参数  不能带括号 

`<input bindinput="handleInput(100)" `     错误写法

2、事件传值  通过标签自定义属性的方式和 `value`

`<input bindinput="handleInput" data-item="100" />`

3、事件触发时获取数据

```js
 handleInput: function(e) {
  // {item:100}
 console.log(e.currentTarget.dataset)

  // 输入框的值
 console.log(e.detail.value);
}
```







## 样式WXSS

WXSS是一套样式语言，用于描述`WXML`的组件样式。

与CSS的不同之处：

- 响应式长度单位`rpx`
- 样式导入

#### 样式尺寸

`rpx`：可以根据屏幕宽度进行自适应。规定屏幕宽度为750`rpx`。



#### 样式导入

使用`@import`语句来导入外联样式表，只支持相对路径。

实例代码：

```css
/** common.wxss **/
.small-p {
 padding:5px;
}
```

```css
/** app.wxss **/
@import "common.wxss";
.middle-p {
 padding:15px;
}
```



#### 选择器

> 小程序不支持通配符`*` 

目前支持的选择器有：

| 类别           | 示例                     | 支持度 |
| :------------- | :----------------------- | :----- |
| 通配选择器     | * {}                     | ×      |
| 元素选择器     | tag {}                   | ✓      |
| 类选择器       | .class {}                | ✓      |
| ID 选择器      | #id {}                   | ✓      |
| 分组选择器     | a, b {}                  | ✓      |
| 直接子代选择器 | a > b {}                 | ✓      |
| 后代选择器     | a b {}                   | ✓      |
| 属性选择器     | [attr] {}                | ×      |
| 一般兄弟选择器 | a ~ b {}                 | ×      |
| 紧邻兄弟选择器 | a + b {}                 | ×      |
| 伪选择器       | :active {} / ::before {} | ×      |





## 常见组件

- ##### [view](https://developers.weixin.qq.com/miniprogram/dev/component/view.html)

代替原来的`div` 标签

```html
 <view hover-class="h-class">
点击我试试
 </view>
```

- ##### [text](https://developers.weixin.qq.com/miniprogram/dev/component/text.html)
  - 文本标签
  - 只能嵌套`text`
  - 长按文字可以复制
  - 可以对空格  回车等进行编码

  ```html
   <text selectable="{{false}}" decode="{{false}}">
   普&nbsp;通
   </text>
  ```

- ##### [rich-text](https://developers.weixin.qq.com/miniprogram/dev/component/rich-text.html)

> 富文本标签

可以将字符串解析成对应标签

- ##### [button](https://developers.weixin.qq.com/miniprogram/dev/component/button.html)

| 属性      | 类型    | 默认值  | 必填 | 说明                                                         |
| :-------- | :------ | :------ | :--- | :----------------------------------------------------------- |
| size      | string  | default | 否   | 按钮的大小                                                   |
| type      | string  | default | 否   | 按钮的样式类型                                               |
| plain     | boolean | false   | 否   | 按钮是否镂空，背景色透明                                     |
| disabled  | boolean | false   | 否   | 是否禁用                                                     |
| loading   | boolean | false   | 否   | 名称前是否带 loading 图标                                    |
| form-type | string  |         | 否   | 用于 [form](https://developers.weixin.qq.com/miniprogram/dev/component/form.html) 组件，点击分别会触发 [form](https://developers.weixin.qq.com/miniprogram/dev/component/form.html) 组件的 submit/reset 事件 |
| open-type | string  |         | 否   | 微信开放能力                                                 |

代码:

```html
<button
 type="default"
 size="{{defaultSize}}"
 loading="{{loading}}"
 plain="{{plain}}"
 >
default
</button>
```



- ##### [image](https://developers.weixin.qq.com/miniprogram/dev/component/image.html)

  - 图片标签，image组件默认宽度320px、高度240px
  - 支持懒加载

  | 属性 | 类型   | 默认值      | 说明                 |
  | :--- | :----- | :---------- | :------------------- |
  | src  | string |             | 图片资源地址         |
  | mode | string | scaleToFill | 图片裁剪、缩放的模式 |

- ##### [navigator](https://developers.weixin.qq.com/miniprogram/dev/component/navigator.html)

> 导航组件  类似于超链接

| 属性      | 类型   | 默认值   | 必填 | 说明                                 |
| :-------- | :----- | :------- | :--- | :----------------------------------- |
| target    | string | self     | 否   | 在哪个目标上发生跳转，默认当前小程序 |
| url       | string |          | 否   | 当前小程序内的跳转链接               |
| open-type | string | navigate | 否   | 跳转方式                             |

open-type的值：

| 合法值       | 说明                                                         |
| :----------- | :----------------------------------------------------------- |
| navigate     | 保留当前⻚⾯，跳转到应⽤内的某个⻚⾯，但是不能跳到tabbar⻚⾯ |
| redirect     | 关闭当前⻚⾯，跳转到应⽤内的某个⻚⾯，但是不允许跳转到tabbar⻚⾯。 |
| switchTab    | 跳转到tabBar⻚⾯，并关闭其他所有⾮tabBar⻚⾯                 |
| reLaunch     | 关闭所有⻚⾯，打开到应⽤内的某个⻚⾯                         |
| navigateBack | 关闭当前⻚⾯，返回上⼀⻚⾯或多级⻚⾯。可通过?getCurrentPages()?获取当前的⻚⾯栈，决定需要返回⼏层 |
| exit         | 退出小程序，`target="miniProgram"`时生效                     |

- ##### [icon](https://developers.weixin.qq.com/miniprogram/dev/component/icon.html)

| 属性  | 类型          | 默认值 | 必填 | 说明                                                         |
| :---- | :------------ | :----- | :--- | :----------------------------------------------------------- |
| type  | string        |        | 是   | icon的类型，有效值：success, success_no_circle, info, warn, waiting, cancel, download, search, clear |
| size  | number/string | 23     | 否   | icon的大小，单位默认为px，2.4.0起支持传入单位(rpx/px)，2.21.3起支持传入其余单位(rem 等)。 |
| color | string        |        | 否   | icon的颜色，同 css 的color                                   |

代码：

```js
Page({
 data: {
  iconSize: [20, 30, 40, 50, 60, 70],
  iconType: [
   'success', 'success_no_circle', 'info', 'warn', 'waiting', 'cancel',
'download', 'search', 'clear'
 ],
  iconColor: [
   'red', 'orange', 'yellow', 'green', 'rgb(0,255,255)', 'blue', 'purple'
 ],
}
})
```



```html
<view class="group">
 <block wx:for="{{iconSize}}">
  <icon type="success" size="{{item}}"/>
 </block>
</view>
<view class="group">
 <block wx:for="{{iconType}}">
  <icon type="{{item}}" size="40"/>
 </block>
</view>
<view class="group">
 <block wx:for="{{iconColor}}">
  <icon type="success" size="40" color="{{item}}"/>
 </block>
</view>
```



- ##### [swiper](https://developers.weixin.qq.com/miniprogram/dev/component/swiper.html)

轮播图

| 属性                   | 类型    | 默认值            | 必填 | 说明                                                         |
| :--------------------- | :------ | :---------------- | :--- | :----------------------------------------------------------- |
| indicator-dots         | boolean | false             | 否   | 是否显示面板指示点                                           |
| indicator-color        | color   | rgba(0, 0, 0, .3) | 否   | 指示点颜色                                                   |
| indicator-active-color | color   | #000000           | 否   | 当前选中的指示点颜色                                         |
| autoplay               | boolean | false             | 否   | 是否自动切换                                                 |
| current                | number  | 0                 | 否   | 当前所在滑块的 index                                         |
| interval               | number  | 5000              | 否   | 自动切换时间间隔                                             |
| duration               | number  | 500               | 否   | 滑动动画时长                                                 |
| circular               | boolean | false             | 否   | 是否采用衔接滑动                                             |
| vertical               | boolean | false             | 否   | 滑动方向是否为纵向                                           |
| previous-margin        | string  | "0px"             | 否   | 前边距，可用于露出前一项的一小部分，接受 px 和 rpx 值        |
| next-margin            | string  | "0px"             | 否   | 后边距，可用于露出后一项的一小部分，接受 px 和 rpx 值        |
| snap-to-edge           | boolean | false             | 否   | 当 swiper-item 的个数大于等于 2，关闭 circular 并且开启 previous-margin 或 next-margin 的时候，可以指定这个边距是否应用到第一个、最后一个元素 |
| display-multiple-items | number  | 1                 | 否   | 同时显示的滑块数量                                           |

```html
<swiper autoplay interval="1000" circular indicator-dots indicator-color="#0094ff" indicator-active-color="#ff0094">
  <swiper-item> 
      <image mode="widthFix" src="bAeF_!!44-0-lubanu.jpg" /> 	
    </swiper-item>
  <swiper-item> 
      <image mode="widthFix" src="pXXSutbFXXX.jpg_q50.jpg" /> 	
    </swiper-item>
  <swiper-item> 
      <image mode="widthFix" src="s1C8zCFJj97b_!!37-0-lubanu.jpg" /> 
    </swiper-item>
</swiper>
```



- ##### [radio](https://developers.weixin.qq.com/miniprogram/dev/component/radio.html)

单选框

代码：

```html
 <radio-group bindchange="handleChange">
  <radio color="red" value="male">男</radio>
  <radio color="red" value="female" >女</radio>
 </radio-group>
 <view>您选中的是:{{gender}}</view>
```

```js
Page({
 data: {
  gender: ""
 },
 handleChange(e){
  // 1 获取单选框中的值
  let gender=e.detail.value;
  // 2 把值 赋值给 data中的数据
  this.setData({
   // gender:gender
   gender
  })
 }
})
```



- ##### [checkbox](https://developers.weixin.qq.com/miniprogram/dev/component/checkbox.html)

复选框

```html
<view>
 <checkbox-group bindchange="handleItemChange">
  <checkbox value="{{item.value}}" wx:for="{{list}}" wx:key="id">
   {{item.name}}
  </checkbox>
 </checkbox-group>
 <view>
  选中的水果:{{checkedList}}
 </view>
</view>
```

```js
Page({
 data: {
  list:[
   {
    id:0,
    name:"🍎",
    value:"apple"
   },
   {
    id:1,
    name:"🍇",
    value:"grape"
   },
   {
    id:2,
    name:"🍌",
    value:"bananer"
   }
  ],
  checkedList:[]
 },
 // 复选框的选中事件
 handleItemChange(e){
  // 1 获取被选中的复选框的值
  const checkedList=e.detail.value;
  // 2 进行赋值
  this.setData({
   checkedList
  })
 }
})
```





## [自定义组件](https://developers.weixin.qq.com/miniprogram/dev/framework/custom-component/)

类似于页面，一个自定义组件由`json`  `wxml`   `wxss`   4个文件组成

在根目录新建components文件夹，进而在此新建各种组件。

##### 1、声明组件

首先在组件的`json` 文件中进行自定义组件声明

```json
{
 "component": true
}
```

##### 2、编辑组件

在组件的`wxml`  文件中编写组件模板，在`wxss` 文件中加入组件样式，`slot`  表示插槽

```html
<view class="inner">
{{innerText}}
  <slot></slot>
</view>
```

> 在组件wxss文件中不应使用ID选择器、属性选择器和标签名选择器。

```css
.inner {
 color: skyblue;
}
```

##### 3、注册组件

在组件的`js`   文件中，需要使用`Component()`  来注册组件，并提供组件的属性定义、内部数据和自定义方法

```js
Component({
 properties: {
  // 这里定义了innerText属性，属性值可以在组件使用时指定
  innerText: {
   // 期望要的数据是 string类型
   type: String,
   value: 'default value',
 }
},
 data: {
  // 这里是一些组件内部数据
  someData: {}
},
 methods: {
  // 这里是一个自定义方法
  customMethod: function(){}
}
})
```

##### 4、声明引入自定义组件

在页面的  `json`    文件中进行引用声明。还要提供对应的组件名和组件路径

`index.wxml`  文件

```json
{
  "usingComponents": {
    "component-tag-name": "path/to/the/custom/component"
  }
}
```

使用组件示例：

```html
<view>
  <!-- 以下是对一个自定义组件的引用 -->
  <component-tag-name inner-text="Some text"></component-tag-name>
</view>
```



自定义组件传参：

- 父传子：父组件通过属性的方式给子组件传递参数

- 子传父：子组件通过事件的方式向父组件传递参数
- 父组件通过`this.selectComponent`  方法获取子组件实例对象，直接访问组件的任意数据和方法

监听事件

```html
<!-- 当自定义组件触发“myevent”事件时，调用“onMyEvent”方法 -->
<component-tag-name bindmyevent="onMyEvent" />
```

```js
Page({
  onMyEvent: function(e){
    e.detail // 自定义组件触发事件时提供的 detail 对象
  }
})
```

触发事件

自定义组件触发事件时，需要使用`triggerEvent`   方法。指定事件名、detail对象和事件选项

```html
<!-- 在自定义组件中 -->
<button bindtap="onTap">点击这个按钮将触发“myevent”事件</button>
```

```js
Component({
  properties: {},
  methods: {
    onTap: function(){
      var myEventDetail = {} // detail对象，提供给事件监听函数
      var myEventOption = {} // 触发事件的选项
      this.triggerEvent('myevent', myEventDetail, myEventOption)
    }
  }
})
```



子传父实例(点击Button修改父组件数据)

`index.wxml`  文件

```html
<component bindTest="hanldeTest" message="{{message}}"></component>
```

`index.js`  文件

```js
Page({
 data: {
  message: "message111"
 },
 hanldeTest(e) {
  this.setData({
   message: e.detail
  })
 }
})
```

`component.wxml`   文件

```html
<view>
 {{message}}
 <button bindtap="handleButton">Button</button>
 <slot></slot>
</view>
```

`component.js`   文件

```js
Component({
 properties: {
  message: {
   type: String,
   value: "default message"
  }
 },
 methods: {
  handleButton(e) {
   this.triggerEvent("Test", "message change");
  },
 }
})
```





## 小程序生命周期

小程序生命周期分为应用生命周期和页面生命周期

#### [应用生命周期](https://developers.weixin.qq.com/miniprogram/dev/reference/api/App.html)



#### [页面生命周期](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html)





### 变量未定义问题

当在data中设置了数据，使用时控制台显示变量未定义，需要在变量名称前添加  `this.data.`  

例如：

```
 data: {
  currentIndex: 0

 },
 Name() {
  const a = this.data.currentIndex
 }
```

