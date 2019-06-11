# Action
除了使用  `find` 方法来查询一个动作，还可以创建一个全局对象 `action`，以便在脚本中获取当前动作的名字和控制流。
## 可调用的实例属性
- `name`_ [动作名字，只读]_
	- 返回动作的名字。
## 可调用的类函数
- `find(name)` -\> _动作_
	- 搜索指定名字的动作。如果找到则返回动作，如果未找到则返回「未定义」。
## 示例
```js
// 搜索动作
var action = Action.find("Copy");
app.queueAction(action, draft);
```
