# systemd配置 

#### 不可直接复制，自己按照情况进行复制、修改

### Renew X

~~~

[Unit]
Description="Microsoft E5 Renew API Web dotnet Service"

[Service]
Type=simple
GuessMainPID=true
WorkingDirectory=/var/www/  #改成网站目录位置
StandardOutput=journal
StandardError=journal
ExecStart=/usr/bin/dotnet Microsoft365_E5_Renew_X.dll
Restart=always

[Install]
WantedBy=multi-user.target

~~~

### Renew Web

~~~

[Unit]
Description="Microsoft E5 Renew API Web dotnet Service"

[Service]
Type=simple
GuessMainPID=true
WorkingDirectory=/var/www/  #改成网站目录位置
StandardOutput=journal
StandardError=journal
ExecStart=/usr/bin/dotnet Microsoft365_E5_Renew_Web.dll
Restart=always

[Install]
WantedBy=multi-user.target

~~~


###### 本系列文档遵循CC-BY-NC-SA-4.0协议 如需转载请遵循。
###### Powered by [docsify](https://docsify.js.org/#/zh-cn/) | Based on [GitHub-Pages](https://github.com/leeskyler-top/Microsoft365-E5Developer-Renew-Web-Docs/)
