# DOMProperty DOM属性

## 释义
bitmask: 位掩码, 掩码是一串二进制代码对目标字段进行位与运算，屏蔽当前的输入位

```javascript
function checkMask(value, bitmask) {
  return (value & bitmask) === bitmask;
}
```


