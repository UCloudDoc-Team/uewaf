# Regional IP Blocking

Regional IP Blocking allows you to specify the domain name for the source request IP address's regional attribution or IDC, ISP information, and choose to allow or block. Allowing is applicable when unblocking a small range of access requests within a large range of blocks.
Regional IP Blocking is controlled by the blacklist and whitelist status and only takes effect when the blacklist and whitelist status is enabled.

![](/images/region_ip-get_rule.png)

> For the priority of various rules, see [Rule Priority](/uewaf/features/rule/mode?id=Rule Priority).

!> Note:  
Regional IP Blocking depends on the accuracy of the IP geographic information database. It is normal for some geographic information to have errors, and we will strive to improve accuracy.

## Add Rule

Rules for domestic or overseas regions support up to 20 regions. When the selected region is a single province, users can choose more municipal regions, but when multiple provincial regions are selected, municipal regions cannot be chosen. The rule for the region's IP information is keyword matching, which will judge the source IP's attribute information (such as IDC, ISP) of the request. If it hits the keyword set by the rule, it will allow or reject the connection according to the rule. **If the action of the rule is to allow, it only means that the request of the IP in this region is not rejected at the stage of Regional IP Blocking judgment, but the request will be judged by the subsequent rules (CC rules, UWAF rules).**

![](/images/region_ip-add_rule.png)

### Rule Parameter Description

| Parameter | Description                                                  |
| --------- | ------------------------------------------------------------ |
| Rule Name | Custom rule name, can be any Chinese or English characters   |
| Region    | Domestic (including Hong Kong SAR, Macao SAR and Taiwan Province), Overseas, IP Information |
| Details   | When the region is domestic or overseas, the specific region selected |
| Keyword   | For IP Information region, custom keyword information        |
| Action    | Reject or allow the connection of the IP that hits the rule  |
