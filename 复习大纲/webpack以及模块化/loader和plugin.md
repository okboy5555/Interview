常见的loader
file-loader：把文件输出到一个文件夹中，在代码中通过相对 URL 去引用输出的文件
url-loader：和 file-loader 类似，但是能在文件很小的情况下以 base64 的方式把文件内容注入到代码中去
source-map-loader：加载额外的 Source Map 文件，以方便断点调试
image-loader：加载并且压缩图片文件
babel-loader：把 ES6 转换成
ES5css-loader：加载 CSS，支持模块化、压缩、文件导入等特性
style-loader：把 CSS 代码注入到 JavaScript 中，通过 DOM 操作去加载 CSS。
eslint-loader：通过 ESLint 检查 JavaScript 代码

常见plugin
define-plugin：定义环境变量
commons-chunk-plugin：提取公共代码
uglifyjs-webpack-plugin：通过UglifyES压缩ES6代码


loader: 是一个nodejs 函数模块， 传入resource file 或者sourceMap json 结果，读取文件，将文件处理为String 或者 Buffer 格式，然后传给compiler 或者下一个loader.

plugin: 是能够参与到compilation process的自定义函数，通过hook到每一个编译（compiler）中，触发关键事件或处理。


编写loader的思路
编写Loader时要遵循单一原则，每个Loader只做一种"转义"工作。 每个Loader的拿到的是源文件内容（source），可以通过返回值的方式将处理后的内容输出，也可以调用this.callback()方法，将内容返回给webpack。 还可以通过 this.async()生成一个callback函数，再用这个callback将处理后的内容输出出去。 此外webpack还为开发者准备了开发loader的工具函数集——loader-utils

如何自定义webpack插件(plugin)：
JavaScript 命名函数
在插件函数prototype 上定义一个apply 方法
定义一个绑定到webpack 自身的hook
处理webpack内部特定数据
功能完成后调用webpack 提供的回调