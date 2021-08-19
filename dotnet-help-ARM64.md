# dotnet ARM64安装方式

1. 前往https://dotnet.microsoft.com/download/dotnet/thank-you/sdk-3.1.412-linux-arm64-binaries下载包
2. 通过各种方式上传到服务器/root/下
3. 使用root运行以下命令
~~~
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.412-linux-arm64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
~~~

## Linux的非apt dnf yum安装方式也可参照这里，但注意此处下载地址为arm64,详情请参照[官网](https://dotnet.microsoft.com/download/dotnet/3.1)

###### 本系列文档遵循CC-BY-NC-SA-4.0协议 如需转载请遵循。

###### Powered by [docsify](https://docsify.js.org/#/zh-cn/) | Based on [GitHub-Pages](https://github.com/leeskyler-top/Microsoft365-E5Developer-Renew-Web-Docs/)
