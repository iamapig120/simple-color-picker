# [Simple Color Picker](https://github.com/iamapig120/simple-color-picker)

- No Flash or images
- No Library Dependencies
- A cursor seems like Photoshop's
- HEX and RGB input
- HEX, RGB and HSB/HSV output
- Styleable flat design in CSS
- Useable in Electron and Browsers

## Demo

[**Please view this page**](https://www.bysb.net/study/color-picker/)
You may view demo's source code to have a mastery of the usage

## Installation & Usage

### Installation

#### Electron Webview

```js
const ColorPicker = require(`./lib/color-picker.js`).ColorPicker
const colorPickerObject = new ColorPicker({
  dom: document.getElementById('colorPicker'), // A DOM Element
  value: '#00FF00' //Same As {r:0,g:255,b:0} and '0F0' and '00FF00'
})
```

#### Browsers

```html
<head>
  <!-- .../ -->
  <!-- Import stylesheet -->
  <link rel="stylesheet" href="./color-picker.css">
  <!-- .../ -->
</head>
```

```html
<body>
  <!-- .../ -->
  <!-- Import script -->
  <script src="./color-picker.js"></script>
  <!-- .../ -->
<body>
```

And then, just instantiation an ColorPicker Object

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
// Create a ColorPicker array
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

// You can get values as "hex", "rgb", "hsb" or just hex color
// Sample
const valueGetSample = new ColorPicker({ value: '#ABC' }) // Same as "#AABBCC"
const hex = valueGetSample.getValue('hex') // "AABBCC"
const rgb = valueGetSample.getValue('rgb') // {r: 170, g: 187, b: 204}
const hsb = valueGetSample.getValue('hsb') // {h: 210, s: 0.16666666666666663, b: 0.8}
const value = valueGetSample.getValue('value') // Same as valueGetSample.value
```
