# Nginx 反向代理配置模版

### 环境：Ubuntu 18.04 apt install nginx (Ubuntu源）

### 请自行修改 server_name（域名或IP）、root（网站目录）、ssl_certificate （pem公钥）、ssl_certificate_key（key私钥）、proxy_pass 、access_log和error_log位置（路径需要存在）

#### 对于Renew X站长的警示语：如需使用Nginx反向代理，请您无论如何在Config.xml中将“Kestrel是否启用HTTPS(SSL加密传输）”设置为true，即使你没有pfx证书，也可使用内建自签证书，即certificate为空.

#### 对于Renew Web用户的警示语：如需使用Nginx反向代理，请您无论如何在Config.json中将UseHttps设置为true，即使你没有pfx证书，也可使用内建自签证书，即UseDevSSL为true.

#### 否则无法使用Oauth登录。

~~~
server
{
    listen 80;
        listen 443 ssl http2;
    server_name 127.0.0.1;
    index index.php index.html index.htm default.php default.htm default.html;
    root /var/www/html/e5.leeskyler.top;
    
    #SSL-START SSL相关配置，请勿删除或修改下一行带注释的404规则
    #error_page 404/404.html;
    #HTTP_TO_HTTPS_START

    if ($server_port !~ 443){
        rewrite ^(/.*)$ https://$host$1 permanent;
    }
    
    #HTTP_TO_HTTPS_END
    ssl_certificate    /var/www/cert/e5.leeskyler.top.pem;
    ssl_certificate_key    /var/www/key/e5.leesyler.top.key;
    ssl_ciphers EECDH+CHACHA20:EECDH+CHACHA20-draft:EECDH+AES128:RSA+AES128:EECDH+AES256:RSA+AES256:EECDH+3DES:RSA+3DES:!MD5;
    ssl_prefer_server_ciphers on;
    ssl_session_cache shared:SSL:10m;
    ssl_session_timeout 10m;
    add_header Strict-Transport-Security "max-age=31536000";
    error_page 497  https://$host$request_uri;

    #SSL-END
    location / {
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header Host $http_host;
    proxy_redirect off;
    proxy_pass https://127.0.0.1:66;
}

    access_log  /var/wwwlogs/e5.leeskyler.top.log;
    error_log  /var/wwwlogs/error/e5.leeskyler.top.error.log;

}

~~~

###### 感谢 七米蓝 为本文档提供临时VPS实践设施 和 对于本Nginx配置文档的实践经验分享

###### 本系列文档遵循CC-BY-NC-SA-4.0协议 如需转载请遵循。

###### Powered by [docsify](https://docsify.js.org/#/zh-cn/) | Based on [GitHub-Pages](https://github.com/leeskyler-top/Microsoft365-E5Developer-Renew-Web-Docs/)

