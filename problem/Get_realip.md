# 获取访问网站的用户的真实IP信息

## WAF获取通过CDN等代理访问的客户端真实IP

一般CDN会通过 XFF(X-Forwarded-For) 或 X-Real-IP 来传递来访客户的真实IP，但是不排除用户构造该字段伪造请求IP的情况出现。

以UCDN举例，如果想在WAF端获取到来访用户的真实的IP，需要做如下操作

1. 在WEB应用防火墙  --->  域名管理，选中需要设置的域名，点击「编辑」
2. 打开后，开启「WAF前是否具有代理」选项，并在「真实IP字段设置」处填入 X-Real-IP 字段（该字段为UCDN传递真实IP客户，如选择其他第三方代理，请与供应商确认真实IP字段）

![](/images/16195047202447.jpg)

3. 配置完成后，点击「确定」，即可在WAF端获取到用户真实IP


## 源站获取客户端真实IP
UWAF会在回源请求头中添加 X-Real-IP 和 X-Forwarded-For 两个字段来传递来访用户的真实IP，在源站服务器中可进行相应的[配置](#示例配置)以便获取这两个字段的值。


### X-Real-IP 与 X-Forwarded-For 的区别

代理服务器（比如UWAF）会把请求的来源IP写入 X-Real-IP 字段，然后发送给源站，这个字段只会有一个IP地址；而每经过一级代理，代理服务器就会把来源追加到 X-Forwarded-For 中，在多次代理的情况下，该字段就会有多个IP地址（真实IP, 代理服务器1, 代理服务器2, ...）。


## 源站获取客户端真实端口

UWAF会在回源请求头中添加 X-Real-Port 字段来传递来访用户的真实端口，源站可通过这个头部字段获取用户客户端真实的端口。

## 示例配置

对于常见的HTTP服务器或Web应用程序，可以通过下面的方法来获取客户端真实IP：

### Nginx

对于Nginx服务器，可以使用 `$http_x_real_ip` 取得 X-Real-IP 字段的值，使用 `$http_x_real_port` 取得 X-Real-Port 字段的值。


若Nginx作为代理服务器，可在配置中添加以下内容使得后端应用能够获取的客户端真实IP

```nginx
# ...
location / {
  # ...

  proxy_set_header Host $host;
  proxy_set_header X-Real-IP $remote_addr;
  proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

  # ...
}
# ...
```

### ASP

```c#
Request.ServerVariables("X-Real-IP")
```

### JSP
```java
request.getHeader("X-Real-IP")
```

### PHP
```php
$_SERVER["X-Real-IP"]
```

?> 注意：如果上层链路为CDN等第三方代理，有可能无法获取真实IP。  
需要提前在域名设置中开启「WAF前是否具有代理」选项并指定客户端真实IP字段。