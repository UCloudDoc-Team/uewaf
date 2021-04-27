# 如何获取访问网站客户的原始IP
UWAF会请求头中通过 X-Real-IP 和 X-Forwarded-For 两个字段来传递来访用户的真实IP，请在源站服务器中配置并获取它们的值。

在Web应用程序中，可以通过下面的方法来获取：

``` html
  –ASP
  Request.ServerVariables(“X-Real-IP”)
  –PHP
  $_SERVER[“X-Real-IP”]
  –JSP
  request.getHeader(“X-Real-IP”)
```

?> 备注：如果上层链路为CDN等第三方代理，有可能无法获取真实IP。
?> 需要提前在域名设置中开启指定获取客户端真实IP字段。

### 如何获取CDN的真实IP？
默认CDN会通过XFF来传递客户的真实IP，但是不排除用户伪造请求IP的情况出现。
以UCDN举例，如果想要用真实的IP进行信息判断，需要做如下操作

1. 在WEB应用防火墙  --->  域名管理，选中需要设置的域名，点击编辑
2. 打开后，开启获取真实IP设置，在真实IP字段填入 X-Real-IP 字段（该字段为UCDN传递真实IP客户，如选择其他第三方代理，请与其供应商确认真实IP字段）
    ![](/images/16195047202447.jpg)

3. 配置完成后，点击确定，即可完成获取真实IP操作


