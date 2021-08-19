# CentOS7 安装dotnet-sdk-3.1的命令

~~~

sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
sudo yum install dotnet-sdk-3.1

~~~

#### 如需CentOS8的安装命令 请前往[官方文档](https://docs.microsoft.com/zh-cn/dotnet/core/install/linux-centos)

#### CentOS8使用DNF 而不是yum,所以请不要想当然修改上面的命令。

#### 官方文档默认演示5.0的安装方式，还请仔细甄别，如安装了错误的dotnet版本，程序是无法运作的。


###### 本系列文档遵循CC-BY-NC-SA-4.0协议 如需转载请遵循。

###### Powered by [docsify](https://docsify.js.org/#/zh-cn/) | Based on [GitHub-Pages](https://github.com/leeskyler-top/Microsoft365-E5Developer-Renew-Web-Docs/)
