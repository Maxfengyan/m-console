aconsole
==============================

一个轻量级的模拟console输出工具用于机顶盒（没用console以及alert环境下）

## 贡献者以及初始构思人: [gongxw](https://github.com/gongxw)
## 特点

- 查看console输出
- 定制化配置

## 功能

- [x] 自定义日志输出背景颜色，位置，大小以及优先级等
- [x] 自定义日志输出文字大小，支持聚焦模式，日志翻页，对象格式化展现便于查看
- [x] 捕捉js执行错误并输出
- [x] 清除日志功能
- [x] 隐藏以及显示日志
- [x] 输出UserAgent

## 使用
```
npm install aconsole
```

引入ist/aconsole.min.js到你的项目中

```html
<script src="path/to/aconsole.min.js"></script>
<script>
  // init vConsole
  
  var _aconsole = new aconsole();
  _aconsole.show()
  _aconsole.log("hello world") 
  _aconsole.trace("hello world") 
  _aconsole.debug("hello world")
  _aconsole.info("hello world")
  _aconsole.warn("hello world")
  _aconsole.error("hello world")
  // example: match key event
  document.addEventListener("keydown", function (event) {
    var code = event.keyCode;
    if (code == 13) {
      // _mconsole.clearAll();
      _mconsole.toggle();
      // _mconsole.clear();
    }
    if (code == 32) {
      _mconsole.log(document.createElement("div"), 2);
    }
    if (code == 34) {
      _mconsole.pageDown();
    }
    if (code == 33) {
      _mconsole.pageUp();
    }
    if (code == 40) {
      _mconsole.moveDown();
    }
    if (code == 38) {
      _mconsole.moveUp();
    }
  });
</script>
```

## 配置

```javascript
var options = {
  position: "left", // 日志输出位置
  size: "50%", // 日志所占屏幕大小
  id: "console", // 日志dom id
  parent: "body", // 捆绑父元素(body, ID, class)
  focus: true, // 聚焦模式, 默认: false
  zindex: 9999, // 默认: 9999
  spread: true, // 默认: false
  bgcolor: "rgba(85,85,85,.8)",
}
new aconsole(options) // unnecessarily
```

## 所有方法
- show() && hide()
- log(data, level) // level: 1: error, 2: warn, 3: info, 4: log, 5: debug, 6: trace
- trace(data)
- debug(data)
- error(data)
- info(data)
- trace(data)
- getDom() // 得到日志dom
- clearAll() // 清除日志
- clear() // 清除当前聚焦的日志, (focus: true)
- pageDown() && pageUp() // 日志翻页
- moveDown() && moveUp() // 聚焦模式下移动焦点 (focus: true)
- toggle() // 格式化当前焦点的日志当当前日志输出为对象的时候 (focus: true)

## toggle before:

<img src="./image/1.jpg">

## toggle after:
<img src="./image/2.jpg">