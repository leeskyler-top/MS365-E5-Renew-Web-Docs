# Supervisor 配置模板

##### 按需修改

##### 请勿直接复制

##### 以Linux格式填写。MacOS请自行甄别。

### Renew X

~~~
[program:RenewX]
command=dotnet Microsoft365_E5_Renew_X.dll
directory=/var/www/MS365E5DRX #程序所在目录
environment=/usr/bin/dotnet #环境变量(通用安装方式请which dotnet检查变量位置)
user=root  #进程执行的用户身份
stopsignal=INT
autostart=true #是否自动启动
autorestart=true #是否自动重启
startsecs=1 #自动重启间隔
stderr_logfile=/var/log/HelloWebApp.err.log #标准错误日志
stdout_logfile=/var/log/HelloWebApp.out.log #标准输出日志
~~~

### Renew Web

~~~
[program:RenewWeb]
command=dotnet Microsoft365_E5_Renew_Web.dll
directory=/var/www/MS365E5DRW #程序所在目录
environment=/usr/bin/dotnet #环境变量(通用安装方式请which dotnet检查变量位置)
user=root  #进程执行的用户身份
stopsignal=INT
autostart=true #是否自动启动
autorestart=true #是否自动重启
startsecs=1 #自动重启间隔
stderr_logfile=/var/log/HelloWebApp.err.log #标准错误日志
stdout_logfile=/var/log/HelloWebApp.out.log #标准输出日志
~~~


###### 本系列文档遵循CC-BY-NC-SA-4.0协议 如需转载请遵循。

###### Powered by [docsify](https://docsify.js.org/#/zh-cn/) | Based on [GitHub-Pages](https://github.com/leeskyler-top/Microsoft365-E5Developer-Renew-Web-Docs/)
