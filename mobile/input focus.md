# input focus

在移动端，有时会出现点击输入框很难聚焦，尤其是快速点击的时候，轻慢点倒时容易让输入框获取焦点。此时可以尝试在输入框外层包上一个div
```html
<div>
  <input />
</div>
```

在div上绑定点击事件，在事件内容调用focus方法让input框获取焦点

不确认是否任何场景都适用，但至少解决了我的问题
