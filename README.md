# BLADELOG
C++ logging library，supports Unicode as well as multithreading


## Platforms
1. Windows 10-11
## Features
1. Color terminal output is supported
2. Custom log output location (terminal/file)

## Usage samples
```cpp
#include "log.h"

/*非线程安全 单例模式*/
#include <process.h>
#include <Windows.h>
#define THREAD_NUM 5

// 全局资源变量
int g_num = 0;

unsigned int __stdcall func(void *pPM)
{
	LOG_INFO("enter");
	//int nThreadNum = *(int *)pPM;
	Sleep(50);
	g_num++;
	LOG_INFO("g_num = %d", g_num);
	LOG_DEBUG("fsafas");
	LOG_INFO("exit");
	LOG_WARNING("!!!");
	LOG_ERROR("xxx");
	return 0;
}

int main()
{
	//LOG *logger = LOG::getInstance(LOG_TARGET_CONSOLE);
	BLADE_CONSOLE_LOG();
	HANDLE  handle[THREAD_NUM];

	//线程编号
	int threadNum = 0;
	while (threadNum < THREAD_NUM)
	{
		handle[threadNum] = (HANDLE)_beginthreadex(NULL, 0, func, NULL, 0, NULL);
		//等子线程接收到参数时主线程可能改变了这个i的值
		threadNum++;
	}
	//保证子线程已全部运行结束
	WaitForMultipleObjects(THREAD_NUM, handle, TRUE, INFINITE);

	//system("pause");
	return 0;
}

```
