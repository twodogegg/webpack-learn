## 1-2 使用 Loader 

在上篇文章中，我们编写了一些 js 文件。在这边文件中我们将会构建一个网页。并为他添加简单的样式

## 安装 Loader
除了 js 文件类型外，webpack  对于其他文件的支持，都需要安装对应的 loader

```bash
yarn add css-loader style-loader -D
```

## 准备代码

src/assets/styles/base.css

```css
body {
    background: red;
}
```

src/main.js

```
require('./module-one')
require('./module-two')

require('./assets/styles/base.css')
```

public/index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>webpack 学习</title>
</head>
<body>

<script src="../dist/bundle.js"></script>
</body>
</html>
```

webpack.config.js 添加如下代码

> `test` 用正则表达式匹配文件后缀， `use` 使用的loader，从上到下执行

```
.
.
.
mode: "development",
module: {
  rules: [
    {
      test: /\.css$/,
      use: [
        'style-loader',
        "css-loader"
      ]
    }
  ]
}
```

## 打包查看效果

```
yarn build
```

打开 `public/index.html` ，将会看到此时的页面背景变成了红色

> 本章代码 [使用 loader](https://github.com/twodogegg/webpack-learn-gitbook-code/tree/use-loader)