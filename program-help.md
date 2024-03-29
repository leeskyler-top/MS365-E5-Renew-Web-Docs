# Renew X与Renew Web程序功能介绍

###### 不介绍用户功能，仅介绍管理员功能

##### *1 补充解释点

以下所有“活动账户”、“活跃用户”均指代微软子账户(租户子账户)（Microsoft365 E5 Developer Accounts）。

## Renew X

### 一、 管理员

- 管理员登陆路由是/Admin/Login

- 管理员只有一名

- 登录管理员->用户列表->为管理员输入OAuth登录关联账户

· GitHub的OAuth ID获取API
~~~
https://api.github.com/users/你的昵称
~~~

输入GitHub-返回的id后面的数字

###### 输入示例：GitHub-00010100

------=====------

· Microsoft的OAuth ID获取API

有一个较为简便的方式 GitHub 也适用。

您可以在自己的站点进行OAuth登录。即可在首页看到OAuth ID了。

输入Microsoft-返回的id后面的数字

###### 输入示例：Microsoft-806ab18b9q2al5g0

###### 警示语：如果站点开启了注册，您需要先关闭注册或在OAuth登录后,前往后台删除此账户,使用“删除数据”

----

### 二、全站查询

- 您可根据需求通过所给方式查询用户，不支持模糊查询，区分大小写。

- 所给方式有 
1. 用户UID
2. OAuth ID
4. 用户名
5. 用户邮箱

##### 管理员自己的UID都是 00000000-0000-0000-0000-000000000000。

##### OAuth ID 填写示例请见第一部分，区分大小写。

##### 用户邮箱就是用户的通知邮箱。

### 三、用户管理

- 账户配额 就是 该账户可调用账户数

- 用户名 通知邮箱可随意更改

- 单击下方调用账户即可修改调用账户、密码、调用方式

- 封禁账户等于删除账户所有有关调用账户的信息。但账户将禁止登录，除非解封。

- 仅在用户要求永久抹除此账户的情况下使用“删除数据”

- 下面是用户绑定的需要活跃的活动账户的列表，点开后可以看到详细信息。

活动账户的颜色有三种情况，绿色代表正常，黄色代表正在等待后台同步。红色代表暂停。

第一行是 本轮此账户总计调用运行数（蓝）| 本轮此账户成功调用数（绿）| 本轮此账户失败调用数（红）

第二行是 本账户在程序运行其间总计调用数（蓝）| 本账户在程序运行其间成功调用数（绿) | 本账户在程序运行其间失败调用数（红）

### 四、运行账户列表

- 显示的是正在运行的活动账户。

- 单击“编辑”可以对活动账户、应用程序ID、账户密码或密钥 进行查看和修改。

- 单击“用户”可以查看此活动账户所属的用户详细信息，可以进行一些用户管理的操作。

### 五、系统设置

- 公告栏信息、推广链接、站长名称 此项功能会默认读取Config.xml 建议在Config.xml内更改，管理面板的信息在系统、程序重启后 会消失！！！它不会计入csv数据库！

- 设置自动特赦时间间隔，届时暂停账户将再次重新尝试运行。

- 立即特赦，所有暂停账户将立即重新尝试运作。

- SMTP回环，用于测试发信邮箱的发件情况，如果不正常，请见本文档 [常见问题->RenewX、Web相关问题->邮件收不到](https://docs-1.leeskyler.top/#/Renew_Web-Questions?id=%e9%82%ae%e4%bb%b6%e6%94%b6%e4%b8%8d%e5%88%b0)。

##### 测试邮件主题：Microsoft365 E5 Renew X 的SMTP测试邮件
##### 测试邮件内容：测试站点：foo 发信时间：YYYY-mm-dd HH:ii:ss UTC时区（服务器时区）

### 六、系统监视

- 蓝色代表总计数 绿色代表成功数 红色代表失败数

- 用于查看程序全局API调用情况 重启系统或程序重置数值。


## Renew Web


### 一、 用户管理 

- 第一个是SundayRX的账户 第二个是你（管理员）自己，管理员不能被删除，在Renew X版本中SundayRX会把自己从程序中删除。
（由于Renew Web属于非公开版，为了方便管理 所以SundayRX把自己写在程序里了）

- 想要指定多管理员，在AdminID一栏用把以前的UID删掉，改成对应的UID，只能新增管理员，不能删除管理员，谨慎操作！！！。

- M开头是微软登录，G开头是GitHub登录

- 每个用户拥有4次被管理员不完全*1删号机会（即5次注册机会）

- 每个用户拥有每天5次编辑配置文件的机会

- 每个用户拥有每天生成5次激活码的机会（即将在Renew X版本中取消此功能，此功能用于旧版Microsoft E5 Renew的激活注册，现在已经停止生命支持。）

- 进入对应用户 在“账户信息”可以看到其调用账户 调用密码 调用方式 暂停通知邮箱

- 运行状态 
 
第一行是 本轮此账户总计调用运行数（蓝）| 本轮此账户成功调用数（绿）| 本轮此账户失败调用数（红）

第二行是 本账户在程序运行其间总计调用数（蓝）| 本账户在程序运行其间成功调用数（绿) | 本账户在程序运行其间失败调用数（红）

- 风险控制 用于重置 注册次数、当日修改次数、生成激活码次数、风控型删除账户*2

下面是具体调用情况。


### 二、风险控制

- 用于记录 所有 已注册成员（包括除管理员现有成员的风控情况，风控型删除账户的风控情况）

- 在成员要求永久抹除账户时，请在此处删除账户*3


### 三、系统设置

- 公告栏信息、最大用户数量 此项功能会默认读取Config.json 按下更新设定更改部分字符如换行需要遵循C#转义符*4 建议在Config.json内更改，管理面板的信息在系统、程序重启后 会消失！！！它不会计入csv数据库！

- 特赦 用于因token失效导致暂停的用户，给予 所有 已暂停 用户重新调用API的能力


### 四、系统监视

- 蓝色代表总计数 绿色代表成功数 红色代表失败数

- 用于查看程序全局API调用情况 重启系统或程序重置数值。


#### 补充解释

*1和*2 同一个东西 此类删号方式会计入风险控制，账户没有被完全抹掉，风险控制 中仍会有记录。

*3 风险控制中删除账户 现有账户将不计入风险控制 同时csv数据库的数据也将一并抹除，谨慎使用。

*4 C# 转义符请参见[下一文档](CSharpSymbol.md)


###### 本系列文档遵循CC-BY-NC-SA-4.0协议 如需转载请遵循。

###### Powered by [docsify](https://docsify.js.org/#/zh-cn/) | Based on [GitHub-Pages](https://github.com/leeskyler-top/Microsoft365-E5Developer-Renew-Web-Docs/)
