# ULB结合UWAF
用户在使用[ULB（请求代理型）](https://docs.ucloud.cn/ulb/intro/architecture?id=%e5%a4%96%e7%bd%91ulb7)服务后，在提高了业务可用性和资源利用率的同时还可以绑定Web应用防火墙（UWAF）得到七层业务的安全防护。

ULB版UWAF在ULB提供的七层转发能力上提供Web安全防护能力，与非ULB版的UWAF相比没有**泛域名、云外源站、查看CC封堵IP、拦截页面、网页防篡改**功能，具体信息请参考[版本选择-功能对比](/uewaf/steer/Version_selection?id=功能说明)，其他功能依靠ULB和UWAF均已实现。


有两种方式可以购买ULB版WAF：  
- [购买UWAF时绑定ULB资源](/uewaf/use/ULB_with_UWAF?id=购买UWAF时绑定ULB资源)  
- [ULB绑定Web应用防火墙](/uewaf/use/ULB_with_UWAF?id=ULB绑定Web应用防火墙)

购买成功并把域名接入UWAF后，日常使用与非ULB版WAF大体一致，但转发面功能如带宽、端口等需到基础网络 UNet控制台或负载均衡 ULB控制台进行调整。

### 注意事项

1. ULB版UWAF目前仅仅支持**广州**区域，其他区域正在逐步支持。  
2. ULB版UWAF的域名、源站、带宽、端口、SSL证书、HTTP2.0、IPv6配置在UWAF控制台无法调整，如需调整，带宽和IPv6配置请到基础网络 UNet控制台，其他配置请到负载均衡 ULB控制台。
3. ULB版UWAF的QPS指标参见ULB的[性能指标](https://docs.ucloud.cn/ulb/intro/performance)。


## 1.购买ULB版WAF

### 购买UWAF时绑定ULB资源

用户可以在「全部产品」选择「Web应用防火墙 UWAF」，点击「开始使用」，在UWAF的购买界面，选择「ULB专区版」进行购买。

采用这种防止购买时，需要提前配置好ULB负载均衡服务，否则无法购买成功。如果您正确配置了ULB服务，可以在 **绑定ULB资源** 一栏下拉看到已配置好的ULB服务，选择需要添加的ULB资源，即可绑定该资源，再根据业务需要选择域名或日志扩展包后点击「立即购买」即可。

![]()

ULB专区版UWAF默认提供20个域名配额，一个域名扩展包可以增加10个域名配置；日志服务默认提供7天内的日志存储与下载，日志扩展包服务则支持最多180天的日志存储与下载。扩展包均是按月计费。

### ULB绑定Web应用防火墙

用户可以在「全部产品」选择「负载均衡 ULB」，点击「创建负载均衡」，在创建负载均衡页面选择「请求代理型」，网络设置根据业务选择，在防火墙一栏选择「绑定Web应用防火墙」，点「立即购买」之后会进入付款界面。创建好负载均衡后，在「负载均衡管理」页面可以看到已有的ULB资源，在防火墙一列可以看到该ULB是否成功绑定了UWAF。


## 2.接入ULB版UWAF

### 负载均衡配置

在ULB控制台的「负载均衡管理」界面选择已绑定UWAF的ULB资源，在操作一栏点击「详情」进行操作，共有三步：

1. 选择「VServer管理」，并点击「添加VServer」，填写 VServer名称 以及 协议和端口，点击「确定」即可，详细说明参见ULB文档：[添加VServer](https://docs.ucloud.cn/ulb/guide/vserver/createvserver)
![ulb_with_uwaf_10](/images/ulb_with_uwaf_10.png)
![ulb_with_uwaf_11](/images/ulb_with_uwaf_11.png)
2. 在「VServer管理」页面选择「服务节点」，点击「添加节点」，将左侧可选资源列出的主机根据业务需要添加到右侧，点击「确定」既可，详细说明参见ULB文档：[添加服务节点](https://docs.ucloud.cn/ulb/guide/realserver/addrealserver)
![ulb_with_uwaf_12](/images/ulb_with_uwaf_12.png)
![ulb_with_uwaf_13](/images/ulb_with_uwaf_13.png)
3. 在「VServer管理」页面选择「内容转发」，点击「添加规则」，根据业务需求填写域名（**UWAF不支持PCRE正则表达式，请填写非正则域名**），将左侧列出的可选节点中的资源根据业务需要添加到右侧的转发节点中，点击「确定」既可，详细说明参见ULB文档：[添加内容转发规则](https://docs.ucloud.cn/ulb/guide/forwardpolicy/addrule)
![ulb_with_uwaf_14](/images/ulb_with_uwaf_14.png)
![ulb_with_uwaf_15](/images/ulb_with_uwaf_15.png)

!> 注意：  
因ULB没有防恶意解析，默认所有请求都会转发到源站，可能会对您的正常业务产生影响，同时考虑到您的Web应用安全，我们强烈建议您参考以下步骤关闭ULB的默认全部转发功能。  
(1) 在「VServer」界面选择「内容转发」，再选择「Default」转发规则，点击「管理」  
(2) 选择右侧的转发节点，点击中间的向左按钮删除该节点  
(3) 重复(2)直到删除所有节点，最后点击「确定」即可关闭ULB的默认全部转发功能  
关闭后若用户访问转发规则里没有的域名时ULB将返回503错误状态码。  
![ulb_with_uwaf_16](/images/ulb_with_uwaf_16.png)
![ulb_with_uwaf_17](/images/ulb_with_uwaf_17.png)

### UWAF配置

在UWAF控制台的「域名管理」界面点击「添加域名」，在弹出的配置界面可以看到已绑定的ULB资源，下拉域名选择需要添加防护的域名，如ULB前有代理服务器如CDN，高防等，需要开启「WAF前是否具有代理」选项并配置正确的代理头，最后点击「确定」即可添加域名，之后通过ULB访问该域名将得到安全防护能力。安全防护配置可参考非ULB版UWAF。

![ulb_with_uwaf_18](/images/ulb_with_uwaf_18.png)
![ulb_with_uwaf_19](/images/ulb_with_uwaf_19.png)

### 修改DNS解析

到您域名的DNS服务商处添加对应域名的A记录，记录值填写ULB所绑定的基础网络的IP地址。

## 解绑和删除

若您想让ULB解绑UWAF，只需在ULB控制台的「负载均衡管理」页面选择对应的ULB资源，点击「详情」后选择「外网防火墙」，解绑对应的Web应用防火墙。

ULB版UWAF的删除需要在UWAF控制台的「域名管理」删除所有域名，最后在「概念」页面点击「关闭UWAF」即可删除UWAF，在扣除已使用时间的折算费用后剩余费用将在1小时内自动返还。
