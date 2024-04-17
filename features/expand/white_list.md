<div id="白名单"></div>

# Whitelist (Domain)

This whitelist is a domain whitelist, different from the [Global Whitelist](/uewaf/global/white_list), the domain whitelist only takes effect for the current domain.

The domain whitelist can allow access requests from specified IP addresses or addresses within the range, without any rule judgment. The domain whitelist is controlled by the blacklist and whitelist status switch, and only takes effect when the blacklist and whitelist status is turned on.

![](/images/white_list-get_domain_rule.png)

> For the priority of various rules, please refer to [Rule Priority](/uewaf/features/rule/mode?id=Rule Priority).

## Rule List

The rule list shows all the blacklist rules under the domain. You can query rules based on remarks, or you can modify or delete rules.

| Parameter  | Description                                                  |
| ---------- | ------------------------------------------------------------ |
| Rule Name  | The name of the whitelist rule, can be any character         |
| IP Content | The specific IP address contained in the rule, can be an IP range or CIDR block |
| IP Type    | The type of IP address in the rule                           |
| Action     | Allow, without any rule judgment                             |
| Join Time  | The time the rule was generated                              |
| Operation  | Edit or delete, you can modify or delete the rule            |

## Add Whitelist

Customize and add domain whitelist rules

![](/images/white_list-add_domain_rule.png)

### Rule Parameter Description

| Parameter  | Description                                                  |
| ---------- | ------------------------------------------------------------ |
| IP Type    | The type of IP address in the rule                           |
| IP Content | The specific IP address contained in the rule, can be an IP range or CIDR block |
| Action     | Allow, without any rule judgment                             |
| Remark     | Mark the rule, can quickly search for rules when there are many rules |

!> Note:  
1 Please select the domain you need to add before adding the domain blacklist and whitelist;
2 The whitelist added is an IP address. If the IP range added to the blacklist contains the IP address of the whitelist, only the specified IP address in the whitelist will be allowed, and the same network segment IP will still be blocked.

## Whitelist Description

1. The maximum number of custom whitelists for each domain refers to [Performance and Quota Comparison](/uewaf/steer/version_selection?id=Performance and Quota Comparison), each entry can contain 200 IPs or IP segments;
2. The priority of the domain whitelist is lower than the global whitelist and higher than the global blacklist and domain whitelist.

<!--

3. The maximum number of machine behavior detections added to the blacklist is 10,000. No merging is performed.
   -->
