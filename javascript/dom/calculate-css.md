# calculate css

-------------------

[TOC]

## 获取css中定义的属性值

```javascript
/**
 * @param  {[type]} elem [description]
 * @param  {[type]} attr [description]
 */
function css(elem, attr) {
  return window.getComputedStyle? getComputedStyle(elem, null)[attr]: elem.currentStyle[attr];
}
```
