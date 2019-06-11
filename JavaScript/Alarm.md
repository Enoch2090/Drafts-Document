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
