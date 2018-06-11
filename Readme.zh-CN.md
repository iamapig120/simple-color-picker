# [Simple Color Picker - 简单的颜色选择器](https://github.com/iamapig120/simple-color-picker)

- 不使用Flash插件或是任何图片
- 无需任何依赖库
- 和Photoshop近似的体验
- 支持 HEX 和 RGB 格式输入
- 支持 HEX, RGB 和 HSB/HSV 输出
- 可监听的 onchange 事件
- 可通过 CSS 自定义的扁平化设计
- 同时可在 Electron 与浏览器中正常工作

## Demo 演示

[**请访问该页面查看在线DEMO**](https://www.bysb.net/study/color-picker/)

您可以通过浏览DEMO页面源代码了解基本的使用方法

## 安装与使用

### 安装

#### Electron Webview

```js
const ColorPicker = require(`./lib/color-picker.js`).ColorPicker
const colorPickerObject = new ColorPicker({
  dom: document.getElementById('colorPicker'), // DOM 对象
  value: '#00FF00' //和 {r:0,g:255,b:0} , '0F0' 以及 '00FF00' 具有相同作用
})
```

#### 浏览器

```html
<head>
  <!-- .../ -->
  <!-- 引入css样式表 -->
  <link rel="stylesheet" href="./color-picker.css">
  <!-- .../ -->
</head>
```

```html
<body>
  <!-- .../ -->
  <!-- 引入JS -->
  <script src="./color-picker.js"></script>
  <!-- .../ -->
<body>
```

然后，您只需要实例化一个 ColorPicker 对象即可

```js
const pickers = [
  new ColorPicker({
    dom: document.getElementById('picker1'),
    value: '#0F0'
  }),
  new ColorPicker({
    dom: document.getElementById('picker2'),
    value: { r: 0, g: 0, b: 255 }
  }),
  new ColorPicker({
    dom: document.getElementById('picker3')
  })
]
```

### Usage

```js
// 创建了一个 ColorPicker 数组
const pickers = [
  new ColorPicker({
    dom: document.getElementById('picker1'),
    value: '#0F0'
  }),
  new ColorPicker({
    dom: document.getElementById('picker2'),
    value: { r: 0, g: 0, b: 255 }
  }),
  new ColorPicker({
    dom: document.getElementById('picker3')
  })
]
pickers.forEach(colorP =>
  colorP.addEventListener('change', event => {
    pickers.forEach(colorPs => {
      if (colorP !== colorPs) colorPs.value = colorP.value
    })
  })
)

// 您可以按照以下多种方式格式化值 "hex", "rgb", "hsb" 或是简单的hex颜色
// 示例
const valueGetSample = new ColorPicker({ value: '#ABC' }) // 与 "#AABBCC" 相同
const hex = valueGetSample.getValue('hex') // "AABBCC"
const rgb = valueGetSample.getValue('rgb') // {r: 170, g: 187, b: 204}
const hsb = valueGetSample.getValue('hsb') // {h: 210, s: 0.16666666666666663, b: 0.8}
const value = valueGetSample.getValue('value') // 与 valueGetSample.value 返回值相同
```
