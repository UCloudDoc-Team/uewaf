# Attack Details

In the attack details, you can view detailed attack behaviors, including attack time, source and destination IP addresses, paths, etc. You can also further view detailed information about attack behaviors or mark some attack behaviors as "false positives".

![](/images/attack_details-query_attack.png)

After expanding the search settings, you can filter the attack details list according to attack type, working mode, matching work, and risk level. After entering the IP address, you can perform a fuzzy search for some IP attack behaviors.

| Attack Information | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Recent Attack Time | The occurrence time of the attack behavior                   |
| Source IP          | The source IP of the attack behavior, if the real IP field is configured, this source IP is the IP address passed by the real IP field |
| Destination IP     | The destination IP of the attack behavior is usually the IP resolved by the CNAME protection domain of the corresponding domain name |
| Request Path       | The request path of the attack behavior, without parameters  |
| Region             | Regional attribution information of the source IP of the attack behavior |
| Attack Count       | The trigger count of the attack behavior                     |
| Working Mode       | The working mode of the corresponding domain name            |
| Matching Action    | The action of the rule matched by this attack behavior, only related to the rule, this item is not affected by the working mode |
| Operation          | Includes two functions: details and false positives          |
| Details            | Detailed information of the attack behavior: <br>● Domain: The domain of the attack request<br>● Request Method: The request method of the attack request, GET, POST, HEAD, etc.<br>● Request Protocol: The request protocol of the attack request, http or https<br>● Request Port: The port requested by the attack request: 80, 443, etc.<br>● Attack Time: The processing time of the attack request<br>● Target IP: The IP requested by the attack request<br>● Client IP: The source IP of the attack request, which may be the IP address of a third-party proxy<br>● Client Port: The source port of the attack request<br>● Region: The regional attribution information of the IP initiating the attack request<br>● Attack Type: The determined type of the attack, CC attack, injection attack, etc.<br>● Risk Level: The severity of the attack, high, medium, low risk<br>● Working Mode: The working mode of the domain name, blocking mode, alarm mode<br>● Matching Action: Whether the rule action matched by the attack request is intercepted or released<br>● Request Path: The path of the attack request, including parameters<br>● Request Content: The body part of the attack request<br>● Request Header(UA): The User-Agent field of the attack request<br>● Referer: The Referer field of the attack request<br>● Proxy IP(XFF): The real IP field of the attack request, if not set, it will be empty<br>● Risk Items: The characteristic characters of the rules triggered in the attack request<br>● Request ID: The string that uniquely identifies this attack request |
| False Positive     | After clicking this button, similar requests will no longer trigger rules, that is, they will no longer be judged as attacks, CC attacks cannot be falsely reported, for details, see [False Positive Details](/uewaf/features/report/false_positive) |

!> Note:  
After clicking [False Positive], the following will happen:
1 Similar attacks will not be displayed in the future, that is, they will no longer be judged as attacks. False positives are based on the characteristics of the attack. If it is a commonly used IP, please add it to the whitelist if you want to release it.
2 Our security engineers will regularly count and analyze the situation of false positives, and continuously update and improve the rule system.
