---
title: 【C++小技巧】How to Format and Get Yesterday Date
date: 2016-08-05 16:01:08
categories: Programming
tags: c++
---

最近工作的时候需要用c++ Format DateTime， 然后上网查了一大圈，发现c++并没有提供一个固定的format方式，boost虽然有format但是感觉有点繁琐。

所以下面提供一下一种比较轻量级的date format的方法。
***
- ##### Format date to YYYY-MM-DD (ex: 2016-01-01)

```c++
#include <stdio.h>
#include <stdlib.h>
#include <sys/time.h>
#include <time.h>

int main(int argc, char *argv[])
{
  time_t rawtime;
  struct tm * timeInfo;
  char buffer [20];

  //get the local date
  time(&rawtime);
  timeInfo = localtime(&rawtime);

  //format the date to YYYY-MM-DD (you can search strftime for more options)  
  strftime(buffer, 20, "%Y-%m-%d", timeInfo);

  std::cout<< buffer << std::endl; //2016-08-05

  return 0;
}
```


- ##### How to get the DateTime of Yesterday

```c++
// Need to add some Code

time(&rawtime);
//Delete total seconds of one day
rawtime -= 86400;
timeInfo = localtime(&rawtime);
```



- ##### How to check if today is Thursday?

```c++
timeInfo = localtime(&rawtime);

//check Thursday
if(timeInfo -> tm_wday == 4) // search to get more options
    std::cout << "Thursday" << std::endl;
else
    std::cout << "Not Thursday" << std::endl;
```

****
