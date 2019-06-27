## 总览
本文档为 Drafts 所使用的 JavaScript 库的中文说明文档。[此处](#)会提供一个目录方便快速索引到特定对象的使用方法。推荐使用 `⌘command - F` 快捷键直接对对应的关键词进行搜索来定位。
### 关于 JavaScript 环境
Drafts 提供的 JavaScript 使用苹果内置的 [ JavaScriptCore ](https://developer.apple.com/documentation/javascriptcore) 作为核心，它提供了对 JavaScript 这门语言完整且现代化的支持，并同时支持 [ECMAScript 6](https://webkit.org/blog/6756/es6-feature-complete/)。
这个编程环境仅支持 JavaScript 语言的核心，不包括 DOM 和 XHTTPRequest 这些经常可以在浏览器中见到的扩展。此处的文档也仅包含 Drafts 特有的库所提供的内容。
目前， 仅有 iOS 版本的 Drafts 支持使用 JavaScript。
### 动作及其执行
Drafts 里的 JavaScript 脚本保存在动作的「Script（脚本）」步骤里，并跟随这些步骤运行。任何包含多个 Script 步骤的动作会获得一个 JavaScript 上下文环境，这些 Script 步骤里的脚本都会在着同一个环境下运行。例如，可以在其中一个 Script 步骤中定义所有的函数，然后在之后的 Script 步骤中调用它们。同样地，在一个 Script 步骤重定义的全局变量也可以在其他 Script 步骤中被调用。