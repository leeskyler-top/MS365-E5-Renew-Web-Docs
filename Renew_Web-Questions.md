# Renew Web或Renew X部署注意事项

### took too long to respond.

检查服务器端口、安全组是否放行，检查程序是否正常运作。

是否用错协议比如https却使用http访问

如果ufw、firewall-cmd等不起作用，请你尝试iptables，呢俩玩意有时会抽风。

### HTTP 500

检查文件是否缺失 Config.json填写方式是否规范。

检查代理、服务器与Oauth服务器通讯情况。

### Cloudflare 400 502 520 521 525

检查SSL设置是否正确

服务器与Cloudflare通讯是否正常

检查端口是否正确，如果非标端口请确保是支持的回源端口

是否用错协议比如https却使用http访问

检查Nginx配置是否正常

检查程序是否正常开启。

检查服务器端口、安全组是否正确放行。

### 请慎重启用Cookie缓存类功能

这可能造成用户登录错乱 甚至是信息泄漏 信息遭到破坏。

### 后端Error: No third-part OAuth login options are enabled.

如果你开启共享站点 则Config.xml中的Microsoft 或 GitHub至少需要启用一个。

### 后端Error: Kerstrel failed to load the "" SSL certificate.

如果你确实需要使用Dev SSL，又出现此报错，我希望你能够尝试运行
~~~
dotnet dev-certs https --trust
~~~

### 后端Error: Kerstrel failed to load the "xxx" SSL certificate.

检查证书格式是否为pfx,使用密码是否正确,文件名拼写是否出错,是否将证书放置在Deploy中。

### 后端Error: The site is shared but HTTPS is not enabled.

开启分享站点 需要开启HTTPS！

###### 本系列文档遵循CC-BY-NC-SA-4.0协议 如需转载请遵循。

###### Powered by [docsify](https://docsify.js.org/#/zh-cn/) | Based on [GitHub-Pages](https://github.com/leeskyler-top/Microsoft365-E5Developer-Renew-Web-Docs/)
