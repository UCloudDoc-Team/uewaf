# ULB结合UWAF
用户在使用[ULB（请求代理型）](https://docs.ucloud.cn/ulb/intro/architecture?id=%e5%a4%96%e7%bd%91ulb7)服务后，在提高了业务可用性和资源利用率的同时还可以绑定Web应用防火墙（UWAF）得到七层业务的安全防护。

ULB专区版UWAF在ULB提供的七层转发能力上提供Web安全防护能力，与非ULB版的UWAF相比没有**泛域名、云外源站、查看CC封堵IP、拦截页面、网页防篡改**功能，具体信息请参考[版本选择-功能对比](/uewaf/steer/Version_selection?id=功能说明)，其他功能依靠ULB和UWAF均已实现。


有两种方式可以接入ULB专区版WAF：  
- [购买UWAF时绑定ULB资源](?id=购买UWAF时绑定ULB资源)  
- [ULB绑定Web应用防火墙](?id=ULB绑定Web应用防火墙)

## 注意事项

1. ULB专区版UWAF目前仅仅支持**广州**区域，其他区域正在逐步适配。  
2. ULB专区版UWAF的带宽、端口、SSL证书、HTTP2.0、IPv6取决于ULB的配置，UWAF控制台无法调整。如需调整，请到ULB控制台。
3. ULB专区版UWAF的QPS指标参见ULB的[性能指标](https://docs.ucloud.cn/ulb/intro/performance)。


## 购买UWAF时绑定ULB资源


## ULB绑定Web应用防火墙

