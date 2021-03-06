# 1.webpack 是什么？
webpack 是一个现代 JavaScript 应用程序的静态模块打包器，当 webpack 处理应用程序时，会递归构建一个依赖关系图，其中包含应用程序需要的每个模块，然后将这些模块打包成一个或多个 bundle。

# 2.webpack 的核心概念
entry: 入口
output: 输出
loader: 模块转换器，用于把模块原内容按照需求转换成新内容
插件(plugins): 扩展插件，在webpack构建流程中的特定时机注入扩展逻辑来改变构建结果或做你想要做的事情

# 0.有哪些常见的Loader？你用过哪些Loader？
* raw-loader：加载文件原始内容（utf-8）
* file-loader：把文件输出到一个文件夹中，在代码中通过相对 URL 去引用输出的文件 (处理图片和字体)
* url-loader：与 file-loader 类似，区别是用户可以设置一个阈值，大于阈值会交给 * * file-loader 处理，小于阈值时返回文件 base64 形式编码 (处理图片和字体)
* source-map-loader：加载额外的 Source Map 文件，以方便断点调试
* svg-inline-loader：将压缩后的 SVG 内容注入代码中
* image-loader：加载并且压缩图片文件
* babel-loader：把 ES6 转换成 ES5
* ts-loader: 将 TypeScript 转换成 JavaScript
* awesome-typescript-loader：将 TypeScript 转换成 JavaScript，性能优于 ts-loader
* sass-loader：将SCSS/SASS代码转换成CSS
* css-loader：加载 CSS，支持模块化、压缩、文件导入等特性
* style-loader：把 CSS 代码注入到 JavaScript 中，通过 DOM 操作去加载 CSS
* postcss-loader：扩展 CSS 语法，使用下一代 CSS，可以配合 autoprefixer 插件自动补齐 CSS3 前缀
* eslint-loader：通过 ESLint 检查 JavaScript 代码
* tslint-loader：通过 TSLint检查 TypeScript 代码

# 1.有哪些常见的Plugin？你用过哪些Plugin？
* html-webpack-plugin：简化 HTML 文件创建 (依赖于 html-loader)
* clean-webpack-plugin: 目录清理
* uglifyjs-webpack-plugin：不支持 ES6 压缩 (Webpack4 以前)
* terser-webpack-plugin: 支持压缩 ES6 (Webpack4)
  
# 2.那你再说一说Loader和Plugin的区别？

Loader 本质就是一个函数，在该函数中对接收到的内容进行转换，返回转换后的结果。
因为 Webpack 只认识 JavaScript，所以 Loader 就成了翻译官，对其他类型的资源进行转译的预处理工作。
Plugin 就是插件，基于事件流框架 Tapable，插件可以扩展 Webpack 的功能，在 Webpack 运行的生命周期中会广播出许多事件，Plugin 可以监听这些事件，在合适的时机通过 Webpack 提供的 API 改变输出结果。
Loader 在 module.rules 中配置，作为模块的解析规则，类型为数组。每一项都是一个 Object，内部包含了 test(类型文件)、loader、options (参数)等属性。
Plugin 在 plugins 中单独配置，类型为数组，每一项是一个 Plugin 的实例，参数都通过构造函数传入。

# 3.Webpack构建流程简单说一下
Webpack 的运行流程是一个串行的过程，从启动到结束会依次执行以下流程：

* 初始化参数：从配置文件和 Shell 语句中读取与合并参数，得出最终的参数
开始编译：用上一步得到的参数初始化 Compiler 对象，加载所有配置的插件，执行对象的 run 方法开始执行编译
* 确定入口：根据配置中的 entry 找出所有的入口文件
* 编译模块：从入口文件出发，调用所有配置的 Loader 对模块进行翻译，再找出该模块依赖的模块，再递归本步骤直到所有入口依赖的文件都经过了本步骤的处理
* 完成模块编译：在经过第4步使用 Loader 翻译完所有模块后，得到了每个模块被翻译后的最终内容以及它们之间的依赖关系
* 输出资源：根据入口和模块之间的依赖关系，组装成一个个包含多个模块的 Chunk，再把每个 Chunk 转换成一个单独的文件加入到输出列表，这步是可以修改输出内容的最后机会
* 输出完成：在确定好输出内容后，根据配置确定输出的路径和文件名，把文件内容写入到文件系统

在以上过程中，Webpack 会在特定的时间点广播出特定的事件，插件在监听到感兴趣的事件后会执行特定的逻辑，并且插件可以调用 Webpack 提供的 API 改变 Webpack 的运行结果。
简单说

* 初始化：启动构建，读取与合并配置参数，加载 Plugin，实例化 Compiler
* 编译：从 Entry 出发，针对每个 Module 串行调用对应的 Loader 去翻译文件的内容，再找到该 Module 依赖的 Module，递归地进行编译处理
* 输出：将编译后的 Module 组合成 Chunk，将 Chunk 转换成文件，输出到文件系统中

# 4.使用webpack开发时，你用过哪些可以提高效率的插件？

* webpack-dashboard：可以更友好的展示相关打包信息。
* webpack-merge：提取公共配置，减少重复配置代码
* speed-measure-webpack-plugin：简称 SMP，分析出 Webpack 打包过程中 Loader 和 Plugin 的耗时，有助于找到构建过程中的性能瓶颈。
* size-plugin：监控资源体积变化，尽早发现问题
* HotModuleReplacementPlugin：模块热替换




