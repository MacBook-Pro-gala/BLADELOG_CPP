# CppLog
A cpp log class that supports Unicode encoding as well as multithreading
## cpplog为LOG类定义了如下级别：

```cpp
enum LOGLEVEL
{
	LOG_LEVEL_NONE,
	LOG_LEVEL_ERROR,     // error
	LOG_LEVEL_WARNING,   // warning
	LOG_LEVEL_DEBUG,     // debug
	LOG_LEVEL_INFO,      // info	
};
```

在软件设计中，可以通过某些方法或者预留一些开关来设置Log级别，方便在开发、调试、测试和客户现场灵活地调整日志级别，以获取到有用的日志信息。
