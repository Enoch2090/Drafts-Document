<head> 
    <script defer src="https://use.fontawesome.com/releases/v5.0.13/js/all.js"></script>  
    <script defer src="https://use.fontawesome.com/releases/v5.0.13/js/v4-shims.js"></script>  
</head> 
<link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.0.13/css/all.css">

# URL Schemes
Drafts 支持基于 [x-callback-url 调用方法](http://x-callback-url.com/) 的唤起动作，它们均以 `drafts5:` 开头。所有的唤起动作链接都遵循如下格式：
```js
drafts5://x-callback-url/[执行操作的名称]?[执行操作的参数]
```
值得注意的是，在所有 Drafts 5 的 URL Schemes 中，`x-callback-url` 这一部分都是可选的。换言之，`drafts5://[actionName]... ` 和 `drafts5://x-callback-url/[actionName]... ` 实现的功能是一样的。
所有调用的 URL 都应该是合法的 URL，其中的内容应该是 URL encode 过的。极少数动作在有些情况下还支持 `x-callback-url `、`x-success`、`x-error ` 和 `x-cancel ` 这些参数。

## 支持的操作
在以下的内容中，我会在操作的名称边附加如下两个标记中的一个或多个：
- 「 <i class="fa fa-mobile"></i>」代表 iOS 版本的 Drafts 支持这个操作。若无此标记出现，则表明 iOS 版本的 Drafts 不支持此动作。
- 「 <i class="fa fa-desktop"></i>」代表 macOS 版本的 Drafts 支持这个操作。若无此标记出现，则表明 macOS 版本的 Drafts 不支持此动作。
### `\create` <i class="fa fa-mobile"></i> <i class="fa fa-desktop"></i>
新建一条草稿，其内容为传递给 `text` 参数的值。如果为 `x-success` 提供地址，
- 参数：
	- `text`_[字符串，必选]_：新建草稿的内容。
	- `tag`_[字符串，可选]_：为新建草稿指定标签。可以使用多个参数，来添加多个标签。
	- `action`_[字符串，可选]_： <i class="fa fa-mobile"></i>  动作的名字。如果提供这个参数，会对新建的草稿运行这个动作。
	- `allowEmpty`_[布尔值，可选]_：如果提供了运行动作的参数，你可以通过添加 `allowEmpty=false` 以便在 `text` 参数为空的时候停止运行动作。这可以防止带有 `x-callback-url` 的动作循环运行。
	- `retParam`_[字符串，可选]_：用于将创建的草稿之 `UUID` 传递回 `x-success-url` 的变量的名称。默认情况下，Drafts 会使用 `uuid` 作为这个变量的名称。但在使用某些应用时可能会对这个变量的名称有所要求（例如「快捷指令」需要这个变量命名为 `input`），你可以使用这个参数来覆盖默认的变量名。
- 示例 ：
	- `drafts5://x-callback-url/create?text=Hello%20World`
		- 创建一条新草稿，其内容为「Hello World」。
### `\open` <i class="fa fa-mobile"></i> <i class="fa fa-desktop"></i>
基于提供的 `UUID` 参数，打开一条已经存在的草稿。
- 参数
	- `uuid`_[字符串，必选]_：需要打开的草稿的 `UUID` 标识符。






