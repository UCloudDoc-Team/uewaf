# 接入 SaaS 版 UWAF

SaaS 版 UWAF 是部署在 Web 服务器前，通过转发代理的方式为业务提供保护的一款产品。通过对流量的内容检测，抵御包括 SQL 注入，XSS 攻击，漏洞攻击，恶意扫描等类型的攻击行为。为网站的正常工作保驾护航。

接入 UWAF 前：
![](/images/access_uwaf-show_before_arch.jpg)

接入 UWAF 后：
![](/images/access_uwaf-show_after_arch.jpg)

## 购买 UWAF

登陆 UCloud 控制台，从产品列表中选择 UWAF：【全部产品】 -> 【安全防护】 -> 【WEB 应用防火墙 UWAF】，再点击【开始使用】（如未开通请先开通该服务）。

![](/images/purchase_waf-purchase_ui.png)

### 参数说明

| 参数                                                             | 说明                                                                                                    |
| ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| 类型                                                             | UWAF 部署的区域类型，包含中国内地，港澳台，海外区域以及 ULB 专区                                        |
| 地域                                                             | 域名配置生成的工作区域                                                                                  |
| 版本类型                                                         | 不同版本 UWAF，详细的版本差异，功能、性能对比，请在[版本选择](/uewaf/steer/version_selection)查看       |
| 扩展带宽                                                         | 当版本提供的带宽额度不满足业务需求时，可提供额外的带宽扩展                                              |
| 域名扩展包                                                       | 当版本提供的域名数不满足业务需求时，可提供额外的域名扩展                                                |
| [独享 IP](/uewaf/features/domain/domain_set?id=exclusive-ip)点数 | 该 IP 点数可为用户域名分配一个独享的 防护 IP ，在版本配额外可提供额外的点数                             |
| 日志扩展包                                                       | 提供 180 天的日志存储与下载服务，满足等保要求，旗舰版及以上赠送日志扩展包                               |
| 高级功能                                                         | 除基本 Web 防护功能外的高级功能，具体说明请在[功能说明](/uewaf/steer/version_selection?id=功能说明)查看 |
| IPv6                                                       | IPV6扩展包，开启后，添加域名时可额外部署到IPv6区域以提供IPv6访问                               |
| 定制化需求                                                       | 可以按需要调整部分无法在控制台调整的功能，详情请咨询技术支持                                            |


购买好合适的 UWAF 后，可按下述步骤将业务接入 UWAF。

## 添加域名

1. 点击【域名管理】->【添加域名】
2. 在弹窗中填写域名和对应域名源站地址，域名可以是泛域名或者完整的子域名。点击【确定】后，在界面上获取生成的 CNAME 信息，域名添加后，可以在【域名管理】对应的域名后点击【编辑】对域名进行更改  
   ![](/images/domain_set-add_domain.png)

3. 域名信息展示  
   ![](/images/domain_set-get_domain.png)

4. HTTPS 站点，需要上传站点的 SSL 证书。若是从[USSL](/ussl/operate/buy)购买的证书或者证书托管在[USSL](/ussl/operate/upload)，则在添加 HTTPS 站点时会自动拉取相应域名的证书。  
   ![](/images/access_uwaf-set_https.png)

域名各配置的[说明](/uewaf/features/domian/domain_set.md)。

!> 注意：  
域名必须是已经备案的，未备案的域名将无法添加。港澳台及海外地区不受备案限制。

## 本地测试

1. 使用 ping 命令获取 CNAME 防护域名 对应的 IP 地址
2. 打开 hosts 文件，修改客户端的 hosts 记录，将站点域名指向第 1)步中所得到的 IP 地址  
   ![](/images/access_uwaf-ping_cname.jpeg)

?> 说明：  
Windows 系统 hosts 文件路径：`c:\windows\system32\drivers\etc\hosts`  
macOS 系统 hosts 文件路径：`/private/etc/hosts`  
Linux 系统 hosts 文件路径：`/etc/hosts`

## 修改 DNS 记录

拿到对应域名的 CNAME 值后，需要到 DNS 服务商处添加 CNAME 记录，将站点的域名正确解析至 UWAF 提供的 CNAME 防护域名 ，如您使用 DNSPod 提供的解析服务，则可以到 DNSPod 控制台添加 CNAME 记录，如下图所示。
![](/images/access_uwaf-set_hosts.jpeg)

### 测试配置是否正确

验证 CNAME 解析是否完成，步骤如下：

1. 在 Windows 操作系统中，使用快捷键 `WIN + R`，在弹出框中输入 `cmd` 并回车；在 Linux 或 macOS 中打开任意终端
2. 执行命令 `nslookup -querytype=cname xxxxxx.uewaf.com`
3. 如果命令执行结果显示了配置的 CNAME 防护域名 或者由 CNAME 防护域名 解析得到的 IP，则表示配置成功

## 模式选择

当用户配置完 DNS 解析后，需要注意查看是否域名已经是阻断模式，如果不是，则需在【防护设置】里选择域名的工作模式为阻断模式。开启 UWAF 的防护功能。
