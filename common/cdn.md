{{indexmenu_n>3}}

# CDN结合UWAF

企业应用防火墙（UWAF），可以与网宿、加速乐、七牛、又拍、阿里云、UCloud等CDN结合使用，对使用了CDN的站点进行WEB应用层的安全防护。

部署架构：

![](/images/common/cdn.png)

### 1.进入UWAF界面

登陆UCloud控制台-U盾-企业应用防火墙UWAF（如未开通请先开通该服务）

### 2.添加域名

在UWAF中点击【添加域名】。在弹窗中填写站点域名，源站IP等信息，域名可以是泛域名或者完整的子域名。点击【确定】后，在界面上获取生成的cname信息。

![](../images/common/waf32.png)

### 3.修改CDN回源域名

修改CDN回源到WAF生成的cname，如果使用的是UCloud的云分发服务，则如下图所示进行修改。

进入：产品与服务->云分发UCDN->域名管理->选中某一个域名->域名配置

注意：

1、 选中的域名要与UWAF中添加的域名一致

2、 源站填写UWAF生成的cname

3、 如果CDN不是从XFF传递的真实客户IP,就有可能导致用户的CDN建邻IP会被误封

![](../images/common/cdn3.png)


