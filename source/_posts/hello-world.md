---
title: 这是我的第一条博客！
date: 2022-09-12
tags: JavaScript
---

## Hello,Welcome to Journey-D's blog!





### JavaScript学习笔记

#### 重绘(Repaint)

**概念：**当一个元素的外观发生改变，但没有改变布局,重新把元素外观绘制出来的过程，叫做重绘。

**常见的引起重绘的属性：**

| 属性：          |       \--        |                 \-- |               \-- |
| --------------- | :--------------: | ------------------: | ----------------: |
| color           |   border-style   |          visibility |        background |
| text-decoration | background-image | background-position | background-repeat |
| outline-color   |     outline      |       outline-style |     border-radius |
| outline-width   |    box-shadow    |     background-size |                   |





### 文档碎片

概念：可以理解为是一个容器，可以临时存放DOM元素。

适用场景：为DOM树新增多个节点时。

若直接将这些节点插入DOM中则会触发多次重排，降低性能，使用文档碎片可以一次性添加多个节点而只触发一次重排，从而达到提升性能的目的（理论上）。

语法：

:one:`let fragment = document.createDocumentFragment();`

:two:`let fragment = new DocumentFragment();`

代码示例：

```
<body>
    <div id="t1">t1</div>
    <button onclick="insert()">insert</button>
    <script>
        function insert() {
            let frag = document.createDocumentFragment()   //新建一个文档碎片
            let p = document.createElement('p')
            p.innerHTML = 'p'
            let div = document.createElement('div')
            div.innerHTML = 'div'
            frag.appendChild(p)                       //在文档碎片中添加元素
            frag.appendChild(div)
            document.querySelector('#t1').appendChild(frag)   //将文档碎片中的元素插入DOM中
        }
    </script>
</body>

```































