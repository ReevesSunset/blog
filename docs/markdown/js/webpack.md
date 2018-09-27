### 基础知识

1. webpack 本身只能处理js文件,处理特定文件要有相应的加载器 loader
2. 还可以通过 loader 引入任何其他类型的文件

### 文件分割

1. spliting
2. CommonsChunkPlugin

### 资源处理

1. 图片静态文件  题外: webpack 根据正则表达式，来确定应该查找哪些文件，并将其提供给指定的 loader。在这种情况下，以 .css 结尾的全部文件，都将被提供给 style-loader 和 css-loader。

2. css中文件的加载 假想，现在我们正在下载 CSS，但是我们的背景和图标这些图片，要如何处理呢？使用 file-loader，我们可以轻松地将这些内容混合到 CSS 中
   css-loader style-loader file-loader
   合乎逻辑下一步是，压缩和优化你的图像。查看 image-webpack-loader 和 url-loader，以了解更多关于如果增强加载处理图片功能。   image-webpack-loader 和 url-loader
   任何类型文件都可以用file-loader来加载

### webpack-dev-server

1. express编写的服务
2. webpack内置 Hot Module Replacement
3. 开启就是在pligins new webpack.HotModuleReplacementPlugin()
4. 命令形式就是 webpack-dev-server --hotOnly


### tree shaking

1. js的未使用的代码,不打包 移除 JavaScript 上下文中的未引用代码(dead-code)

### webpack错误的处理

1. 错误的追踪source map  报错同chrome,报错文件名和行数
2. 配置

``` 
  devtool: 'inline-source-map'  // 仅用于解释说明,不应用与生产环境
```

### 常用的 webpack 插件 plugins

1. HtmlWebpackPlugin 常用的用来在首页引入js的插件
2. clean-webpack-plugin 每次构建前清理dist文件夹

```
    plugins: [
      new CleanWebpackPlugin(['dist']),
      new HtmlWebpackPlugin({
        title: 'Output Management'
      })
    ]
```

### 生产环境构建

1. 生产正式区分环境 webpack4 只需注明mode 即可开箱即用的压缩等
2. 一般会有一个通用配置 webpack-merge

### 命题 webpack与前端工程化

1. 工程化
2. 资源处理
3. 代码运行速度
4. jenkens