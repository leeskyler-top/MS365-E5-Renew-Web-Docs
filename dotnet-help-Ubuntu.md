# Ubuntu 18.04安装命令

~~~

wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
rm packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install -y dotnet-sdk-3.1

~~~

#### 更多版本请查看[官方文档](https://docs.microsoft.com/zh-cn/dotnet/core/install/linux-ubuntu)

#### 但是还请注意官方文档默认5.0 请注意甄别。安装了错误的版本将无法启动本程序。还请谅解。



###### 本系列文档遵循CC-BY-NC-SA-4.0协议 如需转载请遵循。

###### Powered by [docsify](https://docsify.js.org/#/zh-cn/) | Based on [GitHub-Pages](https://github.com/leeskyler-top/Microsoft365-E5Developer-Renew-Web-Docs/)


