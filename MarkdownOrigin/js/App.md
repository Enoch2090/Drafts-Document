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
