# Attack Alert Monitoring

UWAF monitors user domain for attacks. By default, if dangerous attack behaviors (system rules plus user-defined rules) are triggered more than 500 times within 1 minute, an alert email or text message will be sent to the corresponding message subscription group user.

## Handling Attack Alerts

When you receive an attack alert email or text message, please log in to the UWAF console, select "Attack Overview" under "Security Report", select the domain that triggered the alert, set the query time range to the alert triggering period, and you can see the attack situation of this domain during this period.

Select "Attack Details", expand search settings, as shown in the figure below, select the attack type that triggered the alert, and view the specific situation of the attack alert:

![](/images/attack_alert-query_attack.png)

For IPs with a very large number of attacks, you can use the "IP Query" function under "Function Settings" to query the access situation of these IPs during the corresponding period. If you find that this IP has launched a large number of attacks during this period, you can click "Add to Blacklist" in the red box in the figure below to add this IP to the blacklist.

![](/images/attack_alert-query_ip.png)

If there are many attack source IPs, you can use the "Malicious IP Blocking" function under "Protection Settings" to add malicious IP blocking rules and punish IPs with high attack frequency (add to blacklist).
