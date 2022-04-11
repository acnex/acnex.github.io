---
layout: post
title: 关于CSS的定位属性 - Position
date: 2021-04-09 10:55:00
author: 牧之
tags: 
  - CSS
subtitle:   ""
header-style: text
---




position 属性用于表名元素的定位类型，数据类型表示用于设置相对于框的位置的2D空间中的坐标，该属性共有5个值：`static` 、`relative` 、`fixed` 、`absolute` 、`sticky`.

CSS **`position`**属性用于指定一个元素在文档中的定位方式。[`top`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/top)，[`right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/right)，[`bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/bottom) 和 [`left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/left) 属性则决定了该元素的最终位置。

一个偏移量可以是一个相对值用以表示 [`%`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/percentage) （百分比），或是一个绝对的 [`length`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/length) （长度）值。正值是向右或向下的偏移，看适用于哪一个。负值则是在另外方向上的偏移。

### 语法

```css
[ [ left | center | right | top | bottom | <percentage> | <length> ] |
                  [ left | center | right | <percentage> | <length> ] [ top | center | bottom | <percentage> | <length> ] |
                  [ center | [ left | right ] [ <percentage> | <length> ]? ] &&
                  [ center | [ top | bottom ] [ <percentage> | <length> ]? ]
                ]
```

### 1、 静态定位 - static

静态定位是元素的**默认属性**，指定元素使用正常的布局行为，即元素在文档常规流中当前的布局位置。此时 `top`, `right`, `bottom`, `left` 和 `z-index `属性无效。

    ```css
    .class {
        position: static;
    }
    ```

### 2、 固定定位 - fixed

元素会被移出正常文档流，并不为元素预留空间，而是通过指定元素相对于屏幕视口（viewport）的位置来指定元素位置。元素的位置在屏幕滚动时不会改变。打印时，元素会出现在的每页的固定位置。`fixed` 属性会创建新的层叠上下文。当元素祖先的 `transform`, `perspective` 或 `filter` 属性非 `none` 时，容器由视口改为该祖先。

元素的位置相对于**浏览器窗口**是固定位置，元素的位置与文档流无关，Fixed定位的元素和其他元素重叠。

```css
.class {
    position:fixed;
    top:2px;
    right:7px;
}
```

### 3、相对定位 - relative

该关键字下，元素先放置在未添加定位时的位置，再在不改变页面布局的前提下调整元素位置（因此会在此元素未添加定位时所在位置留下空白）。position:relative 对 table-*-group, table-row, table-column, table-cell, table-caption  元素无效。

相对定位元素的定位是相对其正常位置，移动相对定位元素，但它原本所占的空间不会改变。

```html
<div class="box" id="one">One</div>
<div class="box" id="two">Two</div>
<div class="box" id="three">Three</div>
<div class="box" id="four">Four</div>
```

```css
.box {
  display: inline-block;
  width: 100px;
  height: 100px;
  background: red;
  color: white;
}

#two {
  position: relative;
  top: 20px;
  left: 20px;
  background: blue;
}

```



### 4、绝对定位 - absolute

元素会被移出正常文档流，并不为元素预留空间，通过指定元素相对于最近的非 static 定位祖先元素的偏移，来确定元素位置。绝对定位的元素可以设置外边距（margins），且不会与其他边距合并。

绝对定位的元素的位置相对于最近的已定位父元素，如果元素没有已定位的父元素，那么它的位置相对于`<html>`，absolute 定位使元素的位置与文档流无关，因此不占据空间，absolute 定位的元素和其他元素重叠。

```css
.class {
    position:absolute;
    left:70px;
    top:80px;
}
```

### 5、粘性定位 - sticky 

粘性定位的元素是依赖于用户的滚动，在 **position:relative** 与 **position:fixed** 定位之间切换。

它的行为就像 **position:relative;** 而当页面滚动超出目标区域时，它的表现就像 **position:fixed;**，它会固定在目标位置。

元素定位表现为在跨越特定阈值前为相对定位，之后为固定定位。

这个特定阈值指的是 top, right, bottom 或 left 之一，换言之，指定 top, right, bottom 或 left 四个阈值其中之一，才可使粘性定位生效。否则其行为与相对定位相同。

元素根据正常文档流进行定位，然后相对它的*最近滚动祖先（nearest scrolling ancestor）*和 [containing block](https://developer.mozilla.org/en-US/docs/Web/CSS/Containing_block) (最近块级祖先 nearest block-level ancestor)，包括table-related元素，基于`top`, `right`, `bottom`, 和 `left`的值进行偏移。偏移值不会影响任何其他元素的位置。

该值总是创建一个新的[层叠上下文（stacking context](https://developer.mozilla.org/en/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context)）。注意，一个sticky元素会“固定”在离它最近的一个拥有“滚动机制”的祖先上（当该祖先的`overflow` 是 `hidden`, `scroll`, `auto`, 或 `overlay`时），即便这个祖先不是最近的真实可滚动祖先。这有效地抑制了任何“sticky”行为（详情见[Github issue on W3C CSSWG](https://github.com/w3c/csswg-drafts/issues/865)）。

```css
.calss {
    position: sticky;
    top: 10px;
}
```

### 说明

1、大多数情况下，[`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height)和[`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) 被设定为auto的绝对定位元素，按其内容大小调整尺寸。但是，被绝对定位的元素可以通过指定[`top`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/top)和[`bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/bottom) ，保留[`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height)未指定（即`auto`），来填充可用的垂直空间。它们同样可以通过指定[`left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/left) 和 [`right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/right)并将[`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) 指定为`auto`来填充可用的水平空间。

