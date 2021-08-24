# Renew Web或Renew X部署注意事项


## 访问类问题

### took too long to respond.

检查服务器端口、安全组是否放行，检查程序是否正常运作。

是否用错协议比如https却使用http访问。

如果ufw、firewall-cmd等不起作用，请你尝试iptables，呢俩玩意有时会抽风。

### HTTP 500

检查文件是否缺失 Config.json填写方式是否规范。

检查代理、服务器与Oauth服务器通讯情况。

### Cloudflare 400 502 520 521 525

检查SSL设置是否正确。

服务器与Cloudflare通讯是否正常。

检查端口是否正确，如果非标端口请确保是支持的回源端口。

是否用错协议比如https却使用http访问。

检查Nginx配置是否正常。

检查程序是否正常开启。

检查服务器端口、安全组是否正确放行。服务器尝试使用iptables再次放行相应端口。

### Cloudflare 523 Web Server Down 、 Unknown Error

检查程序是否正常运行。

如果使用了Nginx反向代理，检查配置是否正确。

检查访问端口是否受Cloudflare支持。

### 请慎重启用Cookie缓存类功能

这可能造成用户登录错乱 甚至是信息泄漏 信息遭到破坏。


## OAuth类问题

### 微软OAuth登录时出现 invalid_request: The provided value for the input parameter 'redirect_uri' is not valid. The expected value is a URI which matches a redirect URI registered for this client application.

检查应用注册时是否正确填写了Web的Redirect URIs，Platform是否为Web.

### 微软OAuth登录时出现 unauthorized_client: The client does not exist or is not enabled for consumers. If you are the application developer, configure a new application through the App Registrations in the Azure Portal at https://go.microsoft.com/fwlink/?linkid=2083908.

检查Config.xml或Config.json是否正确填写Microsoft 处的 Clientid.

### 微软OAuth登录后出现HTTP 500

检查Config.xml或Config.json是否正确填写Microsoft 处的 SecretKey

### 微软OAuth登录时出现HTTP 500

检查Config.xml是否开启了Microsoft OAuth.

值为false关闭，为true开启，检查拼写是否正确。

### GitHub OAuth登录时出现浏览器HTTP 404 503 或 took too long to respond.

检查OAuth应用 Authorization callback URL是否填写正确。

检查客户端与GitHub通讯是否正常，如不正常请尝试使用代理。

### GitHub OAuth登录时出现GitHub界面的404

检查Config.xml 或 Config.json 是否正确填写GitHub 处的 clientid.

### GitHub OAuth登录时出现浏览器HTTP 500

检查Config.xml 或 Config.json 是否正确填写GitHub 处的 SecretKey.

### GitHub OAuth登录时出现HTTP 500

检查Config.xml是否开启了GitHub OAuth.

值为false关闭，为true开启，检查拼写是否正确。


## 后端报错问题

### 后端Error: No third-part OAuth login options are enabled.

如果你开启共享站点 则Config.xml中的Microsoft 或 GitHub至少需要启用一个。

### 后端Error: Kerstrel failed to load the "" SSL certificate.

如果你确实需要使用Dev SSL，又出现此报错，我希望你能够尝试运行。
~~~
dotnet dev-certs https --trust
~~~

### 后端Error: Kerstrel failed to load the "xxx" SSL certificate.

检查证书格式是否为pfx,使用密码是否正确,文件名拼写是否出错,是否将证书放置在Deploy中。

### 后端Error: The site is shared but HTTPS is not enabled.

开启分享站点 需要开启HTTPS！


## 其他问题

### 邮件收不到

如果是本地邮局、自建邮局，检查相应端口是否开启，并尝试使用iptables再次尝试放行SMTP端口。

如果是本地邮局、自建邮局，检查dovecot、postfix等程序是否正常运行和配置。

部分 自定义域名 托管邮局 请检查DKIM DMARC （自建邮局必须检查rDNS/PTR）记录是否正确配置，否则会被对方邮局拦截。

（部分自定义域名托管邮局不支持设置DKIM DMARC，您可以考虑更换邮局，另外大部分自定义域名托管邮局不支持设置 rDNS/PTR 如微软，您无需检查rDNS/PTR记录。）

检查邮件是否被拦截或邮局限制发送（邮局限制发送如微软A1邮局可能存在过度发信导致邮局禁止发信的问题，你需要发起工单协助）。

检查账户、密码、SMTP地址是否正确，部分邮局需要使用专用密码。

使用telnet检查SMTP地址的25或465或587端口是否正常。

非标端口不受程序支持。

检查邮局是否放行SMTP。

### 如果你排除了上述问题，但问题仍然存在

请检查是否已重启程序。



###### 本系列文档遵循CC-BY-NC-SA-4.0协议 如需转载请遵循。

###### Powered by [docsify](https://docsify.js.org/#/zh-cn/) | Based on [GitHub-Pages](https://github.com/leeskyler-top/Microsoft365-E5Developer-Renew-Web-Docs/)
