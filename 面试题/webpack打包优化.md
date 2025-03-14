# webpack打包优化

1.把多次打包的文件放到同一个文件进行打包

使用**`splitChunks`** 进行代码分割

2.Tree Shaking：

- 移除未使用的代码（Webpack 和 Rollup 默认支持）。

3.压缩代码：

- 使用 Terser 或 UglifyJS 压缩 JavaScript，CSSNano 压缩 CSS。