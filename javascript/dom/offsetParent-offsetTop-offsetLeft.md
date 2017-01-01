# offsetParent, offsetTop, offsetLeft

@(javascript-dom)[offsetParent | offsetTop | offsetLeft]

-------------------

[TOC]

## 获取某个元素距离指定元素（或浏览器）的绝对位移

```javascript
/**
 * 某个元素相对于其偏移参照物的位移
 * @param  {[type]} sElem [source element]
 * @param  {[type]} tElem [target element]
 * @return {[type]}       [{left: ..., top: ...}]
 */
function offset(sElem, tElem) {
  tElem = tElem || document.body;
  var left = sElem.offsetLeft,
      top = sElem.offsetTop,
      parent = sElem.offsetParent,
      isIE8 = window.navigator.userAgent.indexOf('MSIE 8.0') > -1;

  while (!!parent && parent !== tElem && parent !== document.body) {
    if (isIE8) {
      left += parent.offsetLeft;
      top += parent.offsetTop;
    } else {
      left += parent.offsetLeft + parent.clientLeft;
      top += parent.offsetTop + parent.clientTop;
    }

    parent = parent.offsetParent;
  }

  return {left: left, top: top};
}
```

> 注意: 要想绝对的兼容，必须做到以下两点：
> 1. 给获取位置的元素设置相对定位
> 2. 清除body标签的margin
> 3. 清除html标签的margin和padding

## 代码分析

在计算元素到偏移父级元素的距离时，在`IE8`下，`offsetLeft`和`offsetTop`默认是包含偏移父级的`border`的，但是在其他浏览器下，默认是不包含的，所以需要加上`clientLeft`和`clientTop`。

当元素的偏移父级元素是`body`时：
- 如果当前元素是绝对定位或者固定定位，它的`offsetLeft`和`offsetTop`将不会包含`body`的`margin`和`border`（仅在chrome下测试过）
- 如果当前元素没有绝对定位或者固定定位，它的`offsetLeft`和`offsetTop`将会自动包含`body`的`margin`和`border`（仅在chrome下测试过）

> 这里很好理解，因为绝对定位和相对定位的元素，在css中是默认是相对于document.documentElement元素定位的

当元素的偏移父级元素不是`body`时：
- 如果当前是在`IE8`浏览器下，`offsetLeft`和`offsetTop`默认是包含偏移父级的`border`的
- 如果当前不是在`IE8`浏览器下，`offsetLeft`和`offsetTop`不会包含偏移父级的`border`的

`body`元素的`offsetParent`是`null`，`offsetLeft`和`offsetTop`是`0`

