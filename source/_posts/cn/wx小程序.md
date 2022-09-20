---
title: wx小程序
catalog: true
date: 2022-09-20 22:39:45
subtitle: " "
header-img: /img/scenery/wave_bg1.jpg
tags: 微信小程序开发
categories: 小程序
---



## 小程序配置文件

一个小程序应用程序会包含最基本的两种配置文件。一种是全局的`app.json`和页面自己的`page.json`

#### 全局配置`app.json`

`app.json`是当前小程序的全局配置，包括了小程序的所有页面路径、页面表现、网络超时时间、底部tab等。普通快速启动项目里边的`app.json`配置

```
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

1、普通写法

`<view> {{ message }} </view>`

```
Page({
 data: {
  message: 'Hello MINA!'
}
})
```

2、bool类型

`<checkbox checked="{{false}}"> </checkbox>`

3、三元运算

`<view hidden="{{flag ? true : false}}"> Hidden </view>`

4、算数运算

`<view> {{a + b}} + {{c}} + d </view>`

```
Page({
 data: {
  a: 1,
  b: 2,
  c: 3
}
})
```

5、逻辑判断

`<view wx:if="{{length > 5}}"> </view>`

6、字符串运算

`<view>{{"hello" + name}}</view>`

```
Page({
 data:{
  name: 'MINA'
}
})
```

