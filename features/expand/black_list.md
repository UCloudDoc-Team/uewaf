<div id="黑名单"></div>

# Blacklist (Domain)

This blacklist is a domain blacklist, which is different from the [global blacklist](/uewaf/global/black_list). The domain blacklist only takes effect for the current domain.

The domain blacklist can block access requests from specified IP addresses or addresses within the address segment. For requests blocked by the blacklist, UWAF will record the HTTP 444 status code. The domain blacklist is controlled by the blacklist and whitelist status switch, and only takes effect when the blacklist and whitelist status is turned on.

![](/images/black_list-get_domain_rule.png)

> For the priority of various rules, please refer to [Rule Priority](/uewaf/features/rule/mode?id=Rule Priority).

## Rule List

The rule list displays all the blacklist rules under the domain. You can search for rules based on remarks, and you can also modify or delete rules.

| Parameter       | Description                                                  |
| --------------- | ------------------------------------------------------------ |
| Rule Name       | The name of the blacklist rule, which can be any Chinese or English character |
| IP Content      | The specific IP address contained in the rule, which can be an IP address segment or CIDR network segment |
| IP Type         | The type of IP address in the rule                           |
| Action          | Intercept or Verification Code                               |
| Addition Method | Custom addition or automatically added by malicious IP blocking rules |
| Addition Time   | The time when the rule was generated                         |
| Expiration Time | The expiration time of the rule, the rule will be invalid after this time |
| Status          | In effect or expired, only rules in effect have protective effects |
| Operation       | Edit or delete, you can modify or delete rules               |

## Add to Blacklist

Customize the addition of domain blacklist rules

![](/images/black_list-add_domain_rule.png)

### Explanation of Rule Parameters

<!--| Rule Name | The name of the blacklist rule, which can be any Chinese or English character |-->

| Parameter  | Description                                                  |
| ---------- | ------------------------------------------------------------ |
| IP Type    | The type of IP address in the rule                           |
| IP Content | The specific IP address included in the rule, which can be an IP address segment or CIDR network segment |
| Action     | Intercept or captcha<br>● Intercept: Prevent matched requests from accessing all paths under the domain<br>● Captcha: When a matched request is found, a captcha verification page is responded. If the verification fails, it will be intercepted. If the verification passes, the captcha verification page will not be responded to within 10 minutes |
| Valid Time | You can set the effective time of the rule or never expire   |
| Note       | Mark the rule, you can quickly search for rules when there are many rules |

!> Note:  
1 Please select the domain you need to add before adding the domain whitelist and blacklist;
2 The whitelist added is an IP address. If the IP segment added to the blacklist contains the IP address of the whitelist, only the specified IP address in the whitelist will be released, and the remaining IP in the same network segment will still be intercepted.

### Delete Blacklist

After deleting the record of the blacklist, it will no longer intercept or return the captcha interface to the IP or IP segment in this rule.

## Blacklist Explanation

1. The maximum number of custom blacklists for each domain refers to [Performance and Quota Comparison](/uewaf/steer/version_selection?id=Performance and Quota Comparison), and each entry can contain 200 IPs or IP segments;
2. The maximum number of malicious IPs blocked and added to the blacklist is 10,000. Within 1 minute, the same malicious IPs that trigger the rule will be merged and added to the blacklist.

<!--

3. The maximum number of machine behavior detections added to the blacklist is 10,000. No merging process is performed.
   -->
