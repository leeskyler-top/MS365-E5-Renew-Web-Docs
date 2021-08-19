# Microsoft 应用注册

### 普通操作方式（2年需更换密钥）

[单击此处前往](https://portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade)Azure控制台

1. 选择“New registeration” Name随意
2. 选择Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)
3. Redirect URI 输入https://xxx.xxx.xxx/signin-microsoft （请自行替换xxx内容）
4. 进入Certificates & secrets -> New client Secrets -> 名称随意 -> end-date 最高为3年（可使用POST修改时间截）
5. 记录“值”和"client id"
6. 填入Config.json中（Renew X是Config.xml


------------------- 永久密钥获取方式 -----------------------


### 永久密钥获取方式   

不要执行第4、5步
1. 浏览器打开[Microsoft Graph Explorer网页版](https://developer.microsoft.com/en-us/graph/graph-explorer)
2. 左侧单击登录 使用该租户Azure管理员账户登录
3. 赋予所有权限
4. 左侧选择Application(POST)
5. 前往刚刚注册的应用复制ObjectID
6. 回到Microsoft Graph Explorer网页版将其中的URL修改成https://graph.microsoft.com/v1.0/applications/你的ObjectId/addPassword
7.下面全部删除，修改成

~~~
{
"passwordCredential": {
"displayName": "你想要给密钥的描述",
"endDateTime": "2299-12-31T00:00:00Z"
}
}
~~~

下面返回的Secret就是密钥。


###### 本系列文档遵循CC-BY-NC-SA-4.0协议 如需转载请遵循。

###### Powered by [docsify](https://docsify.js.org/#/zh-cn/) | Based on [GitHub-Pages](https://github.com/leeskyler-top/Microsoft365-E5Developer-Renew-Web-Docs/)
