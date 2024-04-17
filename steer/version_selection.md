# Version Selection

If you are a corporate user with certain requirements for disaster recovery and traffic, we recommend you choose the enterprise version of UWAF service. If the business traffic exceeds 100Mbps, it is recommended to choose the appropriate UWAF version based on the size and importance of your business.

The trial version and advanced version are offline, but the configurations of historical users are retained and can still be used. For trial version users who have purchased for more than 3 months, **configuration editing will be restricted**, i.e., adding and modifying configurations will not be possible, but this will not affect the configurations that have already taken effect.

## Version Comparison

!> Note:  
× indicates that this version does not support this feature  
ULB indicates that this item depends on the configuration of ULB""".

### Function Description

| Product Parameter         | Description                                                  | Enterprise Edition | Flagship Edition | Custom Edition | ULB Special Edition |
| ------------------------- | ------------------------------------------------------------ | :----------------: | :--------------: | :------------: | :-----------------: |
| HTTP                      | HTTP(80) port security protection                            |     Supported      |    Supported     |   Supported    |         ULB         |
| HTTPS                     | HTTPS(443) port security protection                          |     Supported      |    Supported     |   Supported    |         ULB         |
| HTTP2.0                   | HTTP2.0 business forwarding and security protection          |     Supported      |    Supported     |   Supported    |         ULB         |
| Non-standard Ports        | Security protection for business ports other than 80, 443    |     Supported      |    Supported     |   Supported    |         ULB         |
| Off-cloud Source Stations | User applications/source stations deployed outside UCloud    |     Supported      |    Supported     |   Supported    |    Not Supported    |
| Basic Protection          | Common Web attacks such as XSS, SQL injection, command execution, etc. |     Supported      |    Supported     |   Supported    |      Supported      |
| Wildcard Domain           | Add wildcard domain for protection                           |     Supported      |    Supported     |   Supported    |      Supported      |
| TLS Configuration         | Can configure global (all domain) TLS version and encryption suite |     Supported      |    Supported     |   Supported    |         ULB         |
| Bandwidth Expansion       | Increase bandwidth beyond the version limit through expansion packs |     Supported      |    Supported     |   Supported    |         ULB         |
| Domain Expansion          | Add more domains beyond the version limit through expansion packs |     Supported      |    Supported     |   Supported    |      Supported      |
| Extra Exclusive IP        | Increase extra exclusive IP points beyond the version limit through expansion packs |     Supported      |    Supported     |   Supported    |    Not Supported    |
| Log Expansion Pack        | Retain logs for 180 days through expansion packs, in compliance with equal protection requirements |     Supported      |    Supported     |   Supported    |      Supported      |
| Custom Protection         | Configure custom protection rules with various conditions    |     Supported      |    Supported     |   Supported    |      Supported      |
| 0Day Protection    | Rapid protection against the latest Web vulnerabilities                    | Supported | Supported | Supported | Supported |
| CC Protection      | Protection against CC attacks, default or custom protection strategies      | Supported | Supported | Supported | Supported |
| CC Block IP   | View or unblock IPs blocked by CC rules            | Supported | Supported | Supported | Not Supported   |
| Malicious IP Blocking | Block IPs that trigger protection rules multiple times         | Supported | Supported | Supported | Supported |
| Regional IP Blocking | Implement access control for specific regions based on rules           | Supported | Supported | Supported | Supported |
| Information Security Protection | Apply protection filters to response content based on rules     | Supported | Supported | Supported | Supported |
| IP Query      | Query IP access, attacks, etc. on domain names         | Supported | Supported | Supported | Supported |
| Blacklist/Whitelist     | Add IPs or IP ranges to block specific IP access       | Supported | Supported | Supported | Supported |
| Log Service     | Real-time log search queries and downloads                 | Supported | Supported | Supported | Supported |
| Certificate Management     | Addition, deletion, and binding of SSL certificates               | Supported | Supported | Supported | ULB  |
| Interception Page     | Custom warning or blocking page after triggering rules         | Not Supported   | Supported | Supported | Not Supported   |
| Web Page Tampering Protection   | Prevent web pages from being tampered to a certain extent                 | Supported | Supported | Supported | Not Supported   |
| Security Alert     | Send security risks or business anomaly alerts via SMS or email | Supported | Supported | Supported | Supported |

<!--
Line 26
| IPv6 | Achieve IPv6 access by purchasing IPv6 extension pack | Support | Support | Support | ULB |
-->

?> Note:  
The available zones currently supported by the ULB special edition can be found at [Price Explanation](/uewaf/steer/price?id=ULB版UWAF).  
Apart from ports below 80, all other ports are supported for non-standard ports.

<!--
IPv6 only supports port 443, please be sure to enable [HTTPS redirection].
The flagship version and the exclusive custom version come with a log extension pack.
-->

<div id="Performance Comparison"></div>

### Performance and Quota Comparison

| Product Parameters                            | Enterprise Edition | Flagship Edition   | Customized Edition  | ULB Zone Edition* |
| --------------------------------------------- | ------------------ | ------------------ | ------------------- | ----------------- |
| Bandwidth<br>(Cloud External/Cloud Internal)  | 40Mbps/<br>120Mbps | 60Mbps/<br>200Mbps | 100Mbps/<br>300Mbps | ULB               |
| Total Domain Number*                          | 20                 | 50                 | 70                  | 20                |
| Pan-Domain Number*                            | 2                  | 5                  | 7                   | 2                 |
| Exclusive IP Points                           | 3                  | 5                  | 10                  | ×                 |
| Domain Deployment Regions                     | 1                  | 2                  | 3                   | ULB Location      |
| QPS                                           | 3000               | 5000               | 10000               | ULB               |
| System Rules (Domain/Item)                    | 20                 | 40                 | 50                  | 20                |
| CC Rules (Domain/Item)                        | 10                 | 20                 | 30                  | 10                |
| CC Protection Peak* (QPS)                     | 50000              | 100000             | 300000              | ULB               |
| Malicious IP Blocking* (Domain/Item)          | 5                  | 5                  | 5                   | 5                 |
| Regional IP Blocking (Domain/Item)            | 10                 | 10                 | 10                  | 10                |
| Information Security Protection (Domain/Item) | 10                 | 20                 | 30                  | 10                |
| IP Query (Item/Day)                           | 30                 | 30                 | 30                  | 30                |
| Black/White List (Domain/Item)                | 500                | 1000               | 3000                | 500               |
| Global Black/White List                       | 10                 | 10                 | 10                  | 10                |
| Log Query and Download                        | Supported          | Supported          | Supported           | Supported         |
| 180-day Log Storage                           | ×                  | Supported          | Supported           | ×                 |
| Web Page Tampering Protection (Domain/Item)   | 20                 | 20                 | 20                  | ×                 |
| Pan-Domain                                    | Supported          | Supported          | Supported           | ×                 |
| Interception Page                             | ×                  | Supported          | Supported           | ×                 |
| Customized Requirements                       | ×                  | Supported          | Supported           | Supported         |

?> Note:  
ULB Zone Edition: The ULB Zone Edition WAF needs to bind at least 1 ULB. If multiple ULBs are bound, they will be billed cumulatively, and the version quota will also accumulate.  
For example, if 2 ULBs are bound, it will cost 7300 yuan/month, and support 40 domain names, other quotas will also double.  
Total number of domain names/Wildcard domain names: For every 10 domain name quotas, 1 wildcard domain name can be added, that is, under normal circumstances, only 2 wildcard domain names can be added to the enterprise edition, and other versions follow this rule.  
CC Protection Peak\*: The CC Protection Peak in the table is a value obtained from **experimental environment** testing. The actual protection peak is related to the network environment, the number of new connections, etc.  
Malicious IP Blocking\*: If the attack type of the rule is "all", only one can be set, and no other rules of attack types can be added. If there are rules for specific attack types, you cannot add rules with the attack type "all".

If the version quota cannot meet your needs, you can purchase an expansion pack. For details, click: [Expansion Pack Function](/uewaf/steer/price?id=Expansion Pack Function)

#### Parameter Description

| Parameter                                    | Description                                                  |
| -------------------------------------------- | ------------------------------------------------------------ |
| Bandwidth<br>(Cloud External/Cloud Internal) | If the source/application is deployed in UCloud (such as UHost) **and is in the same region as the actual deployment of UWAF**, it enjoys internal cloud bandwidth and uses internal cloud bandwidth threshold restrictions. In other cases, it is back to the public network and uses external cloud bandwidth threshold restrictions. If the user's business bandwidth exceeds the version limit, there may be a risk of increased request delay and business link disconnection |
| Number of Domains                            | The maximum number of domains that can be added in the version, every 10 domain quotas can add 1 wildcard domain, the domain quota can be increased by purchasing an expansion pack |
| Exclusive IP Points                          | An exclusive IP point can bind a WAF protection IP to a domain independently. Compared with domains sharing EIP, domains using exclusive IP will not affect other domains when they are under traffic attack. More points can be obtained by purchasing an expansion pack |
| Domain Deployment Region                     | The workspace generated by domain configuration, it is recommended to choose a region close to the source to reduce access latency |
| QPS                                          | The maximum value of the back-to-source QPS supported by the version, QPS is the number of response requests per second, which can represent the maximum throughput. If this limit is exceeded, there may be a risk of increased request delay and business link disconnection |
| System Rules                                 | Customize rules based on fields such as IP, User-Agent, Referer, request method, request content, etc. Each type of field can choose to include, greater than, regular, multi-line matching and other logical conditions |
| CC Rules                                     | Based on the request frequency of the source IP to a certain file or path, block or pop up a captcha to limit the IP with high request frequency |
| CC Protection Peak                           | The maximum number of concurrent links in the current version, if this limit is exceeded, there may be a risk of increased request delay and business link disconnection |
| Malicious IP Blocking                        | Block IPs that trigger protection rules multiple times, IPs that trigger malicious IP blocking rules will be added to the blacklist |
| Regional IP Blocking                         | Judge whether to block or allow the request based on the **origin of the source IP** |
| Information Security Protection              | Desensitize sensitive information such as mobile phone numbers and ID cards to prevent leakage, and can also block based on response content, the format of the response content should be text/html or text/plain. You can also disguise the response content based on the response code of the source station, or change the response to block |
| IP Query                                     | The IP query function can query the basic information of the specified IP, as well as the request statistics of the IP visiting WAF during the specified period |
| Blacklist and Whitelist                      | Requests from IPs or IP segments in the blacklist will be blocked, requests from IPs or IP segments in the whitelist will be allowed, and no security check will be performed |
| Log Query Download                           | By default, you can query the latest 10,000 attack and access logs within 3 days, and you can also download request logs and attack logs within 7 days. If you need longer log storage and download services, please purchase and open the log extension package service (Flagship users are provided with 180 days of log storage for free) |
| 180 Days Log Storage                         | Both attack logs and access logs are stored for 180 days, and users can download the latest 180 days of attack or access logs from the console |
| Web Page Anti-Tampering                      | Add html/htm **static pages** to prevent the page from being maliciously tampered with by hackers |
| Wildcard Domain                              | Add wildcard domains for protection                          |
| Interception Page                            | Customize the warning interception page content triggered by the rule, support html and txt formats |
| Customized Requirements                      | If some functions cannot be adjusted in the console, please consult technical support |
