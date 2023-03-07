# BLADELOG
C++ logging library
Based on the https://blog.csdn.net/sinat_21107433/article/details/103102542

![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/MacBook-Pro-gala/BLADELOG_CPP)

## Platforms
1. Windows 10-11

## Features
1. Color terminal output is supported
2. Custom log output location (terminal/file)
3. support Unicode
4. A more comprehensive definition


## Install
Copy all files to the project
## Usage samples
```cpp
#include "log.h"


#include <process.h>
#include <Windows.h>
#define THREAD_NUM 5


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
	//BLADE_FILE_LOG(); //输出至文件
	BLADE_CONSOLE_LOG(); //输出至终端
	HANDLE  handle[THREAD_NUM];


	int threadNum = 0;
	while (threadNum < THREAD_NUM)
	{
		handle[threadNum] = (HANDLE)_beginthreadex(NULL, 0, func, NULL, 0, NULL);
		threadNum++;
	}
	WaitForMultipleObjects(THREAD_NUM, handle, TRUE, INFINITE);
	return 0;
}

```
