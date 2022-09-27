# 接入 ULB 版 UWAF

用户在使用[ULB（请求代理型）](https://docs.ucloud.cn/ulb/intro/architecture?id=%e5%a4%96%e7%bd%91ulb7)服务后，在提高了业务可用性和资源利用率的同时还可以直接绑定 Web 应用防火墙（UWAF）得到七层 HTTP/HTTPS 业务的安全防护。

ULB 版 UWAF 在 ULB 提供的七层转发能力上提供 Web 安全防护能力，与非 ULB 版的 UWAF 相比没有**云外源站、查看 CC 封堵 IP、拦截页面、网页防篡改**功能，其他功能可参照 UWAF 企业版，具体信息请参考[版本选择-功能对比](/uewaf/steer/version_selection?id=功能说明)。

可以在[购买 UWAF 时绑定 ULB 资源](/uewaf/use/ulb_with_uwaf?id=购买UWAF时绑定ULB资源)，至少需要绑定 1 个 ULB，绑定多个 ULB 采取累积计费，版本配额也会累积。例如绑定 2 个 ULB，则需 7300 元/月，共支持 40 个域名，其他配额也会翻倍。

购买成功并把域名接入 UWAF 后，日常使用与非 ULB 版 WAF 大体一致，但转发面功能如带宽、端口等需到基础网络 UNet 控制台或负载均衡 ULB 控制台进行调整。

若**ULB 已存在且已接入业务**，即为已有的请求代理型负载均衡增加 WAF 防护能力，[可从此步开始](/uewaf/use/ulb_with_uwaf?id=anchor)。

### 注意事项

1. ULB 专区版目前支持的可用区参见[价格说明](/uewaf/steer/price?id=ULB版UWAF)。
2. ULB 版 UWAF 的域名、源站、带宽、端口、SSL 证书、HTTP2.0、IPv6 配置在 UWAF 控制台无法调整，如需调整，带宽和 IPv6 配置请到基础网络 UNet 控制台，其他配置请到负载均衡 ULB 控制台。
3. ULB 版 UWAF 的 QPS 指标参见 ULB 的[性能指标](https://docs.ucloud.cn/ulb/intro/performance)。

## 购买 ULB 版 WAF

### 购买 UWAF 时绑定 ULB 资源

用户可以在【全部产品】选择【Web 应用防火墙 UWAF】，点击【开始使用】，在 UWAF 的购买界面，选择【ULB 专区版】进行购买。

**请先购买 1 个 ULB 资源，否则无法成功购买 ULB 版 WAF**。如果您已购买了 ULB 服务，可以在 **绑定 ULB 资源** 一栏下拉看到已配置好的 ULB 服务，选择需要添加的 ULB 资源，即可绑定该资源，再根据业务需要选择域名或日志扩展包后点击【立即购买】即可。

![](/images/ulb_with_uwaf-purchase_waf.png)

ULB 专区版 UWAF 默认提供 20 个域名配额，一个域名扩展包可以增加 10 个域名配置；日志服务默认提供 7 天内的日志存储与下载，日志扩展包服务则支持最多 180 天的日志存储与下载。扩展包均是按月计费。

## 接入 ULB 版 UWAF

### 负载均衡配置

在 ULB 控制台的【负载均衡管理】界面选择已绑定 UWAF 的 ULB 资源，在操作一栏点击【详情】进行操作，共有三步：

1. 选择【VServer 管理】，并点击【添加 VServer】，填写 VServer 名称 以及 协议和端口，点击【确定】即可，详细说明参见 ULB 文档：[添加 VServer](https://docs.ucloud.cn/ulb/guide/vserver/createvserver)
   ![](/images/ulb_with_uwaf-add_verser_1.png)
   ![](/images/ulb_with_uwaf-add_verser_2.png)
2. 在【VServer 管理】页面选择【服务节点】，点击【添加节点】，将左侧可选资源列出的主机根据业务需要添加到右侧，点击【确定】既可，详细说明参见 ULB 文档：[添加服务节点](https://docs.ucloud.cn/ulb/guide/realserver/addrealserver)
   ![](/images/ulb_with_uwaf-add_verser_3.png)
   ![](/images/ulb_with_uwaf-add_verser_4.png)

<div id='anchor'></div>

3. 在【VServer 管理】页面选择【内容转发】，点击【添加规则】，转发规则选择【域名】，并从右侧下拉框中选择【泛解析】，再填写需要防护的域名（**UWAF 不支持 PCRE 正则表达式，请务必选择【泛解析】**），将左侧列出的可选节点中的资源根据业务需要添加到右侧的转发节点中，点击【确定】既可，详细说明参见 ULB 文档：[添加内容转发规则](https://docs.ucloud.cn/ulb/guide/forwardpolicy/addrule)
   ![](/images/ulb_with_uwaf-add_context_forward_1.png)
   ![](/images/ulb_with_uwaf-add_context_forward_2.png)

!> 注意：  
因 ULB 没有防恶意解析，默认所有请求都会转发到源站，可能会对您的正常业务产生影响，同时考虑到您的 Web 应用安全，我们强烈建议您参考以下步骤关闭 ULB 的默认全部转发功能。  
(1) 在【VServer】界面选择【内容转发】，再选择【Default】转发规则，点击【管理】  
(2) 选择右侧的转发节点，点击中间的向左按钮删除该节点  
(3) 重复(2)直到删除所有节点，再点击【确定】即可关闭 ULB 的默认全部转发功能  
关闭后若用户通过 ULB 访问转发规则里没有的域名时则返回 502 错误状态码。  
![](/images/ulb_with_uwaf-unset_default_forward_1.png)
![](/images/ulb_with_uwaf-unset_default_forward_2.png)

### UWAF 配置

在 UWAF 控制台的【域名管理】界面点击【添加域名】，在弹出的配置界面可以看到已绑定的 ULB 资源，下拉域名选择需要添加防护的域名，如 ULB 前有代理服务器如 CDN，高防等，需要开启【WAF 前是否具有代理】选项并配置正确的代理头，再点击【确定】即可添加域名，之后通过 ULB 访问该域名将得到安全防护能力。安全防护配置可参考非 ULB 版 UWAF。

![](/images/ulb_with_uwaf-add_domain_1.png)
![](/images/ulb_with_uwaf-add_domain_2.png)

### 修改 DNS 解析

如果您的业务已解析到 ULB 上的话，则不需要修改 DNS 解析记录。

如果您的业务还未解析到 ULB 上，您需要到域名的 DNS 服务商处添加对应域名的 A 记录，记录值填写 ULB 所绑定的基础网络的 IP 地址。

## 解绑和删除

若您想让 ULB 解绑 UWAF，只需在 ULB 控制台的【负载均衡管理】页面选择对应的 ULB 资源，点击【详情】后选择【外网防火墙】，解绑对应的 Web 应用防火墙。

ULB 版 UWAF 的删除需要在 UWAF 控制台的【域名管理】页面删除所有域名，再在【概览】页面点击【关闭 UWAF】即可删除 UWAF，在扣除已使用时间的折算费用后，剩余费用将在 1 小时内自动返还。
