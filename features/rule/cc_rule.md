# CC Rules

CC rules can limit the rate of requests to prevent a large number of requests from directly reaching the origin server, causing network congestion or a surge in CPU usage at the origin server.

> For the priority of various rules, please refer to [Rule Priority](/uewaf/features/rule/mode?id=Rule Priority).

## CC Protection Modes and Status

CC protection modes include normal mode and emergency mode:

- **Normal**: Only custom rules are effective (if there are no custom rules, only the default rule is effective).
- **Emergency**: Not only will custom rules take effect, but UWAF will also intercept requests of abnormal frequency based on data analysis, artificial intelligence recognition, and other technologies, but there may be false positives. In emergency mode, UWAF will automatically intercept based on attack characteristics, and will add a cookie parameter to the request for verification. If the website has a 301 redirect, it is not recommended to enable emergency mode.

The default status of CC is enabled. At this time, if the user has not configured CC rules, a default rule will take effect. The default rule is: if the number of requests from a single IP exceeds 500 times in 1 minute, the request from this IP will be intercepted for 10 minutes. **This default rule is forcibly enabled when the user has not added a custom CC rule**. If the user adds any custom CC rule, the default rule will not take effect. **If the CC status is closed, UWAF will not provide CC protection capability, please choose carefully**.

For all CC rules, the CC protection engine will count any request, but when a rule is triggered, it will **not intercept** the access of common static types of files, the specific file types are `css, ico, png, jpg, js, gif`. If you need to enable the interception of such files, please consult technical support.

## Custom CC Rule List

The CC rule list displays the custom rules added by the user. After adding a custom rule for a certain file or subdirectory, for security reasons, we recommend that you add another catch-all rule, that is, set a rule that a single IP accesses the root directory (/) more than 1000 times in a certain period of time (such as 60 seconds). This can effectively deal with the situation where the attacker changes the attack path to carry out a CC attack.

![](/images/cc_rule-get_rule.png)           

## Add Rules

![](/images/cc_rule-add_rule.png)

​                                                       

### Explanation of Rule Parameters

| Parameter     | Explanation                                                  |
| ------------- | ------------------------------------------------------------ |
| Rule Name     | The name of the custom rule, can be any Chinese or English character |
| Limit Rate    | The access threshold for a single IP within the statistical period |
| Limit Feature | The request path is a required item, and its limit logic is either exact match (equals) or directory match (contains). Other limit fields refer to [Matching Condition Explanation](/uewaf/features/rule/uwaf_rule?id=Matching Condition Explanation). The logic between multiple limit features is 'and' |
| Limit Method  | The restriction measures taken for IPs that exceed the limit rate and meet the limit features, including the following methods:<br>● Block this IP: 4-layer block; if there are proxies such as CDN in front, the IP address of the link will be blocked, that is, the IP of the CDN and other proxy nodes, **causing a large area to be unable to access normally, please use with caution**, the default restriction time is 2 hours, this time cannot be changed<br>● Intercept such requests: 7-layer block, UWAF will reject the requests of the blocked IP and record the HTTP 444 status code; if there are proxies such as CDN in front, you need to correctly configure [Real IP Field Settings], if the CDN and other proxies do not correctly pass this field, there may be false positives<br>● Enable captcha: Redirect to the captcha page, if the user passes the verification, this IP will be whitelisted for 10 minutes (CC rule judgment is not performed, other rule judgments are not affected)<br>● Limit request rate: Limit the request rate according to the rule's limit rate, that is, it will judge whether the number of requests in the statistical period before the request arrives exceeds the access limit number. If it does not exceed, it will not be restricted. If it exceeds, it will respond with HTTP 429 status code. The restriction time of this method is invalid, no attack log is recorded, and the access log can be filtered by the 429 status code to query the IP that triggers the rule<br>● Only record logs: Only record a CC attack log, do not take substantial restriction measures |
| Limit Time    | The effective time of the rule, after which the IP will be re-judged for CC rules |

## CC Blocked IP

Here you can see the list of IPs that triggered the CC rules, including blocked or captcha-triggered IPs. [Refresh CC Blacklist] will cancel all IP bans or captcha verifications, and the [Unblock this IP] operation in the operation column can cancel the ban or captcha verification of a single IP. The refresh blacklist or unblock IP operation may be delayed, and the actual effective time shall prevail.

![](/images/cc_rule-get_blocked_ip.png)

## CC Rule Examples

1. If the access situation of a certain business domain name has always been stable, a single IP will not exceed 100 times in 1 minute, and you want to use UWAF to resist potential CC attacks.  
   Rule example:

   - Rule Name: Anti-CC Rule
   - Limit Rate: Single IP accesses 100 times in 60 seconds
   - Limit Feature: Request path directory matches / (directory match plus root directory equals the whole site)
   - Limit Method: Intercept such requests
   - Limit Time: 1440 minutes

   Situation: When a malicious client sends 100 requests in 30 seconds, this CC rule will be triggered, and the source IP address of this malicious client will be blocked for 24 hours. After that, all requests from this IP address to this business domain name will respond with HTTP 444 status code.

2. If an online mall domain name is going to hold a product seckill event, it is expected that there will be a large number of customers visiting during the scheduled period, causing a surge in traffic, and you want to use UWAF for access throttling.

- Rule example (1):

  - Rule Name: Throttling Rule 1
  - Limit Rate: Single IP accesses 20 times in 60 seconds
  - Limit Feature: Request path directory matches A path (the path where the seckill product belongs)
  - Limit Method: Enable captcha
  - Limit Time: 3 minutes

- Rule example (2):

  - Rule Name: Throttling Rule 2
  - Limit Rate: Single IP accesses 20 times in 60 seconds
  - Limit Feature: Request path directory matches A path (the path where the seckill product belongs)
  - Limit Method: Limit request rate
  - Limit Time: 120 minutes

  Situation (1): For rule example (1), when a client sends 20 requests in 30 seconds, this CC rule will be triggered, and the source IP address of this client will initiate the 21st request, UWAF will redirect this request to the captcha page. If the verification is passed, the requests from this IP address will not be judged by the CC rules within the next 10 minutes; if the verification is not passed, then UWAF will continue to redirect the requests from this IP address to this online mall's domain name to the captcha page within the limit time.  
  Situation (2): For rule example (2), when a client sends 20 requests in 30 seconds, this CC rule will be triggered, and the source IP address of this client will initiate the 21st request, UWAF finds that this IP address has sent 20 requests in these 60 seconds, so it responds to this request with HTTP 429 status code. If UWAF does not receive a request from this IP address within 60 seconds, this client can continue to request this online mall, but the number of requests within 60 seconds cannot exceed 20 times.
