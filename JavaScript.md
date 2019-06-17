# 总览
Drafts 提供的 JavaScript 使用【】作为核心，共支持
目前， 仅有 iOS 版本的 Drafts 支持使用 JavaScript。
## 标记说明

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
# ActionGroup
代表一个动作组。这个对象可以用来搜索动作组，并在之后使用 `App` 这个对象中的方法来加载找到的动作组。
## 可调用的实例属性
- `name` _[动作组名字，只读]_
	- 返回动作组的名字。
## 可调用的类函数
- `getAll()` -\> _以列表形式返回动作组对象_
	- 获取所有可用的动作组。
- `find(name)` -\> _动作组_
	- 搜索指定名字的动作。如果找到则返回动作，如果未找到则返回「未定义」。

## 示例
```js
// 搜索动作组
var group = ActionGroup.find("Basic"); //搜索「Basic」这个动作组，并赋值给变量「group」
app.loadActionGroup(group);
```
# Alarm
`Alarm` 可以将提醒附加到系统自带的「提醒事项」，或添加到日历中的事件上。需要搭配 `ReminderList` 或 `Calender` 对象来使用。
## 可调用的类函数
- `alarmWithDate(日期)`  -\> _输出一个提醒_
	- 将提醒设置为指定的日期。
- `alarmWithOffset(秒数)` -\> _输出一个提醒_
	- 将提醒设置在事件开始日期过指定秒数之后。**注意：这种方式创建的提醒只支持日历的事件，不支持提醒事项。**
## 示例
```js
var list = ReminderList.findOrCreate("Errands");
var reminder = list.createReminder();
reminder.title = "Get more paper towels";

var alarm = Alarm.alarmWithDate((3).days().fromNow());
reminder.addAlarm(alarm);

reminder.update();
```
# App
Drafts 提供了 `App` 这个对象，它可以让用户访问应用级别的功能。
## 可调用的实例属性
- `version`_[字符串，只读]_
	- 返回当前草稿的版本号。
- `themeMode`_[字符串]_
	- 获取/设置当前的主题模式。可选的模式有：
		- light（明亮模式）
		- dark（黑暗模式）
		- automatic（自动设置）
- `currentThemeMode`_[字符串，只读]_
	- 返回当前激活的主题模式。这一实例会同时参考当前是否开启了「自动设置」功能。如果想要让脚本根据当前的主题模式运行分支，这是最适合使用的实例。 
isDraftListVisible [boolean, readonly](#)
Is the draft list side panel is visible.
isActionListVisible [boolean, readonly](#)
Is the action list side panel is visible.
isIdleDisabled [boolean](#)
Is system sleep timer disabled preventing screen dimming/sleep.
