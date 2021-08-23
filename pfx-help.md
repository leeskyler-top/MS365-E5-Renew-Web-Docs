# pem公钥 key私钥 (crt证书)转换pfx

##### Renew Web & Renew X 采用kerstrel 需要pfx证书，使用 有效签名证书 或 自定义证书 均需要将 pfx证书 放在 Deploy 目录下面。在Config文件中相应位置进行填写。

##### 如果你没有域名可以在freenom搞个免费的，实在不想用域名又要用HTTPS，还搞不到有效证书的话，我建议你用自签证书。

##### 本页面为有效签名证书或自定义证书设置，如您只是使用系统自签证书则无需查看此页面。

pem公钥 key私钥 (crt证书)

#### 服务器内需要有openssl

#### 没有openssl需要安装

### CentOS7
~~~
yum install openssl
~~~

### CentOS8 
~~~
dnf install openssl
~~~

### Ubuntu 
~~~
apt install openssl
~~~
### 转换命令
~~~
openssl pkcs12 -export -out 想要的文件名.pfx -inkey 文件名.key -in 文件名.pem -certfile 文件名.crt
~~~
-certfile变量在某些时候不需要。

接下来你需要输入两次使用密码，可以输出空值。

如果您不需要使用密码
~~~
openssl pkcs12 -passout pass: -export -out 想要的文件名.pfx -inkey 文件名.key -in 文件名.pem -certfile 文件名.crt
~~~


###### 感谢 七米蓝 为本文档提供临时VPS实践设施 和 对于不需要使用密码变量的经验分享

###### 本系列文档遵循CC-BY-NC-SA-4.0协议 如需转载请遵循。

###### Powered by [docsify](https://docsify.js.org/#/zh-cn/) | Based on [GitHub-Pages](https://github.com/leeskyler-top/Microsoft365-E5Developer-Renew-Web-Docs/)
