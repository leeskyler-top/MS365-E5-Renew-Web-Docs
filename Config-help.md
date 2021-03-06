# Config 各项目解释

## --Renew X

#### 提供预览。

#### 警告：由于jsdelivr掉了备案被间歇性屏蔽，我们更换了bootstrap5的CDN，为了防止CDN再次出事或者太慢，我们在最新版提供了CDN外部链接更新接口，可按需更改，请注意Bootstrap版本必须是5.1.3。

#### 警告：如果您所使用的的域名有备案，请务必填写“网站备案”部分。

~~~
<?xml version="1.0" encoding="utf-8" ?>
<Configuration>
	<!--站点服务器基本配置-->
	<Serivce>
		<!--服务访问端口-->
		<Port>1066</Port>
		<!--管理员密码(管理员登录路由/Admin/Login) 重要：首次启动前必须更改-->
		<LoginPassword>12345678</LoginPassword>
		<!--是否启用内核多线程支持-->
		<CoreMultiThread>true</CoreMultiThread>
		<!--网站备案（选填）-->
		<ICP>
			<!--备案显示文本-->
			<Text></Text>
			<!--备案管理查询机构跳转链接-->
			<Link>https://beian.miit.gov.cn</Link>
		</ICP>
		<!--Bootstrap CDN 若要更改请务必使用bootstrap@5.1.3版本（选填）-->
		<CDN>
			<!--Bootstrap CSS文件CDN bootstrap.min.css-->
			<CSS>https://cdn.staticfile.org/bootstrap/5.1.3/css/bootstrap.min.css</CSS>
			<!--Bootstrap JS文件CDN bootstrap.bundle.min.js-->
			<JS>https://cdn.staticfile.org/bootstrap/5.1.3/js/bootstrap.bundle.min.js</JS>
		</CDN>
	</Serivce>
	<!--站点Kestrel服务器HTTPS配置 （只支持IIS证书类型 即PFX格式的证书）-->
	<HTTPS>
		<!--Kestrel是否启用HTTPS(SSL加密传输)-->
		<Enable>false</Enable>
		<!--SSL证书文件名 (需要将PFX格式的SSL证书放置于该配置文件的同级目录Deploy文件夹下) 如e5.sundayrx.net.pfx-->
		<!--不填则默认使用Dev localhost 本地证书-->
		<Certificate></Certificate>
		<!--SSL证书密钥(PFX证书的访问密钥)-->
		<Password></Password>
	</HTTPS>
	<!--共享站点配置,不共享可无视以下内容 (若要共享站点 请自备以下所需的配置信息 且配置中HTTPS必须启用)-->
	<ShareSite>
		<!--是否启用站点共享-->
		<Enable>false</Enable>
		<!--SMTP邮件发送支持-->
		<SMTP>
			<!--发件邮箱-->
			<Email></Email>
			<!--邮箱密钥-->
			<Password></Password>
			<!--SMTP服务器地址-->
			<Host></Host>
			<!--SMTP服务器端口-->
			<Port>587</Port>
			<!--SMTP服务器是否使用SSL传输-->
			<EnableSSL>true</EnableSSL>
		</SMTP>
		<!--第三方OAuth登录支持(至少启用以下一种OAuth否则其他用户无法注册)-->
		<OAuth>
			<!--微软登录授权-->
			<Microsoft>
				<!--是否启用该OAuth-->
				<Enable>true</Enable>
				<!--应用程序Id-->
				<ClientId></ClientId>
				<!--应用程序访问机密-->
				<ClientSecret></ClientSecret>
			</Microsoft>
			<!--GitHub登录授权-->
			<Github>
				<!--是否启用该OAuth-->
				<Enable>true</Enable>
				<!--应用程序Id-->
				<ClientId></ClientId>
				<!--应用程序访问机密-->
				<ClientSecret></ClientSecret>
			</Github>
		</OAuth>
		<!--站点系统设置-->
		<System>
			<!--站点启动后默认是否允许用户注册 建议为false-->
			<AllowRegister>false</AllowRegister>
			<!--站点启动后默认公告（换行符请使用 &#x000D;&#x000A; 进行换行）-->
			<Notice></Notice>
			<!--站点运营者-->
			<Master></Master>
			<!--站点运营者推广链接-->
			<MasterLink></MasterLink>
			<!--站点新用户默认配额数-->
			<DefaultQuota>1</DefaultQuota>
			<!--站点自动特赦时间间隔 （单位：天 至少30天）-->
			<AutoSpecialPardonInterval>30</AutoSpecialPardonInterval>
		</System>
	</ShareSite>
</Configuration>
~~~

#### Renew X采用xml,里面有注释

#### 另外xml无法直接使用回车，也无需参照C#转义符，仅需在对应位置键入`&#x000A;&#x000D;&#x000A;&#x000D;`即可换一行。


## --Renew Web

##### 请勿复制

~~~
{
   "UseHttps": true,      //Https启用或关闭，由于本发行版本为群管群主的私配版本，只支持Oauth登录，Oauth的相关规范要求必须使用HTTPS，如果不使用Nginx/Apache/Caddy等程序SSL反向代理，此项必须为true.
    "Port": "",            //默认66
    "SSL": {
        "UseDevSSL": false,      //如果没有有效证书，可以true启用程序自带的自签证书
        "SSLFileName": "",       //UseHttps为false或UseDevSSL为true情况下此项目无效，此项为pfx证书文件名，请放在Deploy文件夹下
        "SSLFilePassword": ""    //pfx证书使用密码
        },
  "Authentication": {              
    "Microsoft": {
      "ClientId": "",            //Microsoft Azure应用ID    
      "ClientSecret": ""         //Microsoft Azure应用Secret
    },
    "GitHub": {
      "ClientId": "",            //GitHub Oauth ID 
      "ClientSecret": ""         //GitHub Oauth Secret
    }
  },
  "SMTP": {
    "Email": "",                 //邮箱账户，部分大厂邮局需要对账户放行SMTP使用许可，比如QQ邮箱。
    "Password": "",              //部分大厂邮局需要有专用密码
    "Host": ""                   //SMTP服务器，不需要填端口 25 465 587自动的，不能非标端口
  },
    "AdminID": "",
    "AllowMaxUserNum": "",       //允许最大人数
    "WebMaster": "",             //必填 管理员昵称 全英语尽量无其他字符 用于右下角显示
    "WebMasterURL": "",          //鼠标在页面右下角管理员昵称上停留时，预重定向的链接，非必填，可以是自己的博客也可以是其他链接
    "CoreMultiThread": true,     //多线程是否启用 启用true 不启用false 一般为true
    "BulletinMessage":""         //公告，非必填/r/n换行，部分字符需要遵循C# 转义符才能显示。
}

~~~


###### 本系列文档遵循CC-BY-NC-SA-4.0协议 如需转载请遵循。
###### Powered by [docsify](https://docsify.js.org/#/zh-cn/) | Based on [GitHub-Pages](https://github.com/leeskyler-top/Microsoft365-E5Developer-Renew-Web-Docs/)

