# CDN 结合 UWAF

?> 说明：  
基于 SaaS 版 UWAF。

Web 应用防火墙（UWAF），可以与网宿、加速乐、七牛、又拍、阿里云、UCloud 等 CDN 结合使用，对使用了 CDN 的站点进行 WEB 应用层的安全防护。

## 部署架构

![](/images/cdn_wite_uwaf-show_arch.jpg)

## 购买 UWAF

登陆 UCloud 控制台，从产品列表中选择 UWAF：【全部产品】 -> 【安全防护】 -> 【WEB 应用防火墙 UWAF】，再点击【开始使用】（如未开通请先开通该服务）。

## 添加域名

在 UWAF 控制台的【域名管理】标签页中中点击【添加域名】，在弹窗中填写站点域名，源站 IP 等信息，域名可以是泛域名或者完整的子域名。点击【确定】后，在界面上获取生成的 CNAME 信息。

!> 注意：  
域名必须是已经备案的，未备案的域名将无法添加。海外地区不受备案限制。  
如果防护的是 HTTPS 站点，需要上传站点的 SSL 证书。若是从[USSL](/ussl/operate/buy)购买的证书或者证书托管在[USSL](/ussl/operate/upload)，则在添加 HTTPS 站点时会自动拉取相应域名的证书。

## 修改 CDN 回源域名

修改 CDN 回源到 UWAF 生成的 CNAME，如果使用的是 UCloud 的 UCDN 云分发服务，则如下面流程所示进行修改：  
控制台左上方【全部产品】-> 【云分发 UCDN】-> 【域名管理】-> 选中某一个域名 -> 点击【详情】->【域名配置】->【基础设置】->修改【源站】为从 UWAF 控制台得到的 CNAME 防护域名 。
![](/images/cdn_with_uwaf-set_cdn.jpg)

### 注意事项

1. CDN 的域名要与 UWAF 中添加的域名一致
2. 源站填写 UWAF 生成的 CNAME
3. 如果 CDN 不是从 XFF 传递的真实客户 IP，则有可能导致用户的 CDN 建邻 IP 会被误封
