# 客户端真实 IP 及端口

## UWAF 获取通过 CDN 等代理服务器访问的客户端真实 IP

一般 CDN 会通过 XFF(X-Forwarded-For) 或 X-Real-IP 来传递来访用户的真实 IP，但是不排除用户构造该字段伪造请求 IP 的情况出现。

以 UCDN 举例，如果想在 WAF 端获取到来访用户的真实的 IP，需要做如下操作

1. 打开 WEB 应用防火墙控制台的【域名管理】，选中需要设置的域名，点击【编辑】
2. 打开后，开启【WAF 前是否具有代理】选项，并在【真实 IP 字段设置】处填入 X-Real-IP 字段（该字段为 UCDN 传递用户真实 IP 的字段，如选择其他第三方代理，请与供应商确认真实 IP 字段）

![](/images/16195047202447.jpg)

3. 配置完成后，点击【确定】，即可让 UWAF 获取到客户到客户端真实 IP。

## 源站获取客户端真实 IP

UWAF 会在回源请求头中添加 X-Real-IP 和 X-Forwarded-For 两个字段来传递来访用户的真实 IP，在源站服务器中可进行相应的[配置](#示例配置)以便获取这两个字段的值。

#### X-Real-IP 与 X-Forwarded-For 的区别

代理服务器（比如 UWAF）会把请求的来源 IP 写入 X-Real-IP 字段，然后发送给源站，这个字段只会有一个 IP 地址；而每经过一级代理，代理服务器会把来源追加到 X-Forwarded-For 中，在多次代理的情况下，则该字段会有多个 IP 地址（真实 IP, 代理服务器 1, 代理服务器 2, ...）。

## 源站获取客户端真实端口

UWAF 会在回源请求头中添加 X-Real-Port 字段来传递来访用户的真实端口，源站可通过取这个头部字段的值获取用户客户端真实的端口。

## 示例配置

对于常见的 HTTP 服务器或 Web 应用程序，可以通过下面的方法来获取客户端真实 IP：

#### Nginx

对于 Nginx 服务器，可以使用 `$http_x_real_ip` 取得 X-Real-IP 字段的值，使用 `$http_x_real_port` 取得 X-Real-Port 字段的值。利用 Nginx 的 `http_realip_module` 模块可以让 `$remote_addr` 显示为客户端的真实 IP，添加的配置如下：

```nginx
set_real_ip_from 回源IP段; # 回源IP段可在控制台 概览 页的 基本信息 处查看，多个IP段需多条指令。
real_ip_header X-Forwarded-For; # 也可以使用 X-Real-IP
real_ip_recursive on; # 若WAF前有CDN等代理，需要此指令设为 on，否则不用。
```

若源站的 Nginx 作为代理服务器，在前文配置的基础上还可在配置中添加以下内容使得后端应用也能通过 X-Real-IP 或 X-Forwarded-For 获取的客户端真实 IP：

```nginx
# ...
location / {
  # ...
  proxy_set_header Host $host;
  proxy_set_header X-Real-IP $remote_addr;
  proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
}
# ...
```

#### ASP

```c#
Request.ServerVariables("X-Real-IP")
```

#### JSP

```java
request.getHeader("X-Real-IP")
```

#### PHP

```php
$_SERVER["X-Real-IP"]
```

?> 说明：  
如果上层链路为 CDN 等第三方代理服务器，有可能无法获取真实 IP。此种情况需要参照前文[WAF 获取通过 CDN 等代理服务器访问的客户端真实 IP](/uewaf/problem/Get_realip?id=WAF获取通过CDN等代理访问的客户端真实IP)提前在域名设置中开启【WAF 前是否具有代理】选项并指定客户端真实 IP 字段。
