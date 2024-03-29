# 高防服务结合 UWAF

?> 说明：  
基于 SaaS 版 UWAF。

UCloud 高防服务和 Web 应用防火墙（UWAF）是完全兼容的。

## 部署架构

![](/images/ddos_with_uwaf-show_arch.jpeg)

## 购买 UWAF

登陆 UCloud 控制台，从产品列表中选择 UWAF：【全部产品】 -> 【安全防护】 -> 【WEB 应用防火墙 UWAF】，再点击【开始使用】（如未开通请先开通该服务）。

## 添加域名

在 UWAF 控制台的【域名管理】标签页中中点击【添加域名】，在弹窗中填写站点域名，源站 IP 等信息，域名可以是泛域名或者完整的子域名。点击【确定】后，在界面上获取生成的 CNAME 信息。

!> 注意：  
域名必须是已经备案的，未备案的域名将无法添加。港澳台及海外地区不受备案限制。
如果防护的是 HTTPS 站点，需要上传站点的 SSL 证书。若是从[USSL](/ussl/operate/buy)购买的证书或者证书托管在[USSL](/ussl/operate/upload)，则在添加 HTTPS 站点时会自动拉取相应域名的证书。

## 域名测试

PING CNAME 防护域名 得到分配的 UWAF 的 IP

## 修改高防源站 IP

1. 配置高防，源站 IP 填写刚才得到的 UWAF 的 IP
2. 点击确定后，会生成高防的 CNAME 地址
3. 后续配置 DNS，将需要防护的域名解析到高防 CNAME，即可完成配置
