# Renew X & Renew Web启动提示（这不是帮助）

## Linux & Windows

### 如果您已制作了进程守护

- Linux用户可以使用systemctl start xxxx.service

(xxxx指的是您创建service文件的文件名）

- Windows用户可以使用Scheduled Task(计划任务界面）

选中您刚刚创建的任务，在右边单击启动即可

### 如果您没有制作进程守护

##### 无论您是什么系统 什么架构

请打开Shell(终端)

~~~
cd 到程序所在路径
~~~

- Renew X启动命令

~~~
dotnet Microsoft365_E5_Renew_X.dll
~~~

- Renew Web启动命令

~~~
dotnet Microsoft365_E5_Renew_Web.dll
~~~


###### 本系列文档遵循CC-BY-NC-SA-4.0协议 如需转载请遵循。

###### Powered by [docsify](https://docsify.js.org/#/zh-cn/) | Based on [GitHub-Pages](https://github.com/leeskyler-top/Microsoft365-E5Developer-Renew-Web-Docs/)
