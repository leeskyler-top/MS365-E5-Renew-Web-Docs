# Windows 计划任务配置无图指南

在网站目录下创建start.bat


### 如果安装 Renew X

#### 里面输入 dotnet Microsoft365_E5_Renew_X.dll

### 如果安装Renew Web

#### 里面输入 dotnet Microsoft365_E5_Renew_Web.dll

Ctrl + S 保存
Win + R

输入“Control”

搜索“计划任务”

选择“创建任务”

选择“不管用户是否登录都运行”

勾选“影藏”（可选）

选择“触发器”->“新建”

开始任务选择"启动时"

选择“操作”->“新建”

选择“浏览” 到达start.bat所在路径并选择start.bat

确定后 在 起始位置输入网站目录

确定



###### 本系列文档遵循CC-BY-NC-SA-4.0协议 如需转载请遵循。

###### Powered by [docsify](https://docsify.js.org/#/zh-cn/) | Based on [GitHub-Pages](https://github.com/leeskyler-top/Microsoft365-E5Developer-Renew-Web-Docs/)


