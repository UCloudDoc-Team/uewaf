# 接入SaaS版UWAF
SaaS版UWAF是部署在Web服务器前，通过转发代理的方式为业务提供保护的一款产品。通过对流量的内容检测，抵御包括SQL注入，XSS攻击，漏洞攻击，恶意扫描等类型的攻击行为。为网站的正常工作保驾护航。

![](/images/15970482393080.jpg)

接入UWAF前后对比：

![](/images/15970482669463.jpg)

## 1.进入UWAF控制台
登陆UCloud控制台，从产品列表中选择UWAF：【全部产品】 -> 【安全防护】 -> 【WEB应用防火墙 UWAF】，再点击【开始使用】（如未开通请先开通该服务）。

![access_uwaf_1_purchase_ui.png](/images/access_uwaf_1_purchase_ui.png)

### 参数说明

|参数|说明|
|-|-|
|类型|UWAF部署的区域类型，包含中国内地，港澳台，海外区域以及ULB专区|
|地域|域名配置生成的工作区域|
|版本类型|不同版本UWAF，详细的版本差异，功能、性能对比，请在[版本选择](/uewaf/steer/Version_selection)查看|
|扩展带宽|当版本提供的带宽额度不满足业务需求时，可提供额外的带宽扩展|
|域名扩展包|当版本提供的域名数不满足业务需求时，可提供额外的域名扩展|
|[独享IP](/uewaf/features/domain/Domain_set?id=exclusive-ip)点数|该IP点数可为用户域名分配一个独享的防御IP，在版本配额外可提供额外的点数|
<!--|IPv6|IPV6扩展包，开启后，添加域名时可额外部署到IPv6区域以提供IPv6访问|-->
|日志扩展包|提供180天的日志存储与下载服务，满足等保要求，旗舰版及以上赠送日志扩展包|
|高级功能|除基本Web防护功能外的高级功能，具体说明请在[功能说明](/uewaf/steer/Version_selection?id=功能说明)查看|
|定制化需求|可以按需要调整部分无法在控制台调整的功能，详情请咨询技术支持| 


## 2.添加域名
1). 点击【域名管理】->【添加域名】  
2). 在弹窗中填写域名和对应域名源站地址，域名可以是泛域名或者完整的子域名。点击【确定】后，在界面上获取生成的CNAME信息  
![](/images/16062909081477.jpg)

3). 域名信息展示  
![](/images/15970491668107.jpg)

4). HTTPS站点，需要上传站点的SSL证书。若是从[USSL](/ussl/operate/buy)购买的证书或者证书托管在[USSL](/ussl/operate/upload)，则在添加HTTPS站点时会自动拉取相应域名的证书。   
![](/images/16062908633019.jpg)

域名各配置的[说明](/uewaf/features/domian/Domain_set.md?id=parameter-1)。

!> 注意：  
域名必须是已经备案的，未备案的域名将无法添加。  
海外地区不受备案限制。


## 3.本地测试
1). 使用ping命令获取CNAME防护域名对应的IP地址  
![](/images/16062912982683.jpeg)
2). 打开hosts文件，修改客户端的hosts记录，将站点域名指向第1)步中所得到的IP地址  
![](/images/16062913664718.jpeg)

?> 说明：  
Windows系统hosts文件路径：``c:\windows\system32\drivers\etc\hosts``  
macOS系统hosts文件路径：``/private/etc/hosts``  
Linux系统hosts文件路径：``/etc/hosts``

## 4.修改DNS记录
拿到对应域名的CNAME值后，需要到DNS服务商处添加CNAME记录，将站点的域名正确解析至UWAF提供的CNAME，如您使用 DNSPod 提供的解析服务，则可以到 DNSPod 控制台添加CNAME记录，如下图所示。
![](/images/16062914733087.jpg)

## 5.测试配置是否正确
验证CNAME的解析是否完成，步骤如下：

1). 在Windows操作系统中，使用快捷键 ``WIN + R``，在弹出框中输入 ``cmd`` 并回车；在 Linux 或 macOS 中打开任意终端  
2). 执行命令  ``nslookup -querytype=cname xxxxxx.uewaf.com``  
3). 如果命令执行结果显示了配置的CNAME防护域名或CNAME防护域名解析得到的IP，则表示配置成功  
![](/images/15970493399116.jpg)


## 6.模式选择
当用户配置完DNS解析后，需要注意查看是否域名已经是阻断模式，如果不是，则需在【防护设置】里选择域名的工作模式为阻断模式。开启UWAF的防护功能。
