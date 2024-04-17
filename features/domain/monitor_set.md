# Parsing and Monitoring Settings

[Parse Settings](#Parse Settings), according to the function configuration, parse the service request to high defense, WAF, source station. It fits the user's application scenario more closely, increasing the flexibility and security of WAF configuration.  
[Monitoring Settings](#Monitoring Settings), according to the application scenarios of different domains, users can configure the monitoring method for the corresponding domain separately, in order to obtain relevant alarm information in time.

!> Note:  
For monitoring settings, except for automatic return to source in case of business exceptions, all other types of monitoring are controlled by the switch in the [Global Alert Settings](/uewaf/global/message/alert). Here is only the sub-switch at the domain level. If the corresponding switch in the global alert settings is not turned on, you will not be able to receive SMS or email alert notifications.
When the parsing status is "high defense", the automatic return to source mode does not take effect.

## Parse Settings

After successfully creating a domain name, you can configure the domain name parsing in List Page → More → Parse Settings, the default is WAF parsing.  

Parsing status: The pop-up window shows the parsing status of all regions of the current domain.  

(1) High Defense: Parse the domain name to the corresponding high defense IP.  

(2) Normal: Parse the domain name to WAF.  

(3) Returned to Source: The domain name is directly parsed to the source IP.  
![](/images/monitor_jxsz1.png)""".

### WAF Parsing

After successfully creating a domain name, you can go to List Page→More→Parsing Settings→Domain Name Parsing (default configuration).

In this mode, UWAF will identify and block malicious requests, and protect the domain name according to the corresponding protection rule strategy.
![](/images/monitor_wafjx.png)


### Source Station Parsing

Configuration path: List Page→More→Parsing Settings→Source Station Parsing.

In this mode, the client will directly access the source station, and the source station will lose the protection of WAF, please configure carefully.

![](/images/monitor_yzjx.png)

### High Defense Parsing

Configuration path: List Page→More→Parsing Settings→High Defense Parsing.
In this mode, UWAF and UDDOS work together to provide DDOS protection and attack protection for the source station.

!> Note:   
This mode requires users to purchase [UDDOS](/uantiddos/uantiddos) service and complete related configurations to be implemented.  
Only domain names that have enabled the high defense parsing function can enjoy DDOS protection.

![](/images/monitor_gfjx1.png)

#### High Defense Settings

Configuration path: Domain Name List→More→High Defense Settings.  

![](/images/monitor_gfjx2.png)

#### High Defense Configuration

High Defense Configuration: Click the [High Defense Configuration] button to pull up the configuration pop-up window, which cannot be configured under the high defense parsing status.  
Mode:  
①Manual: Users manually switch to high defense, which will point DNS parsing to the high defense IP, and notify users after successful configuration.  
②Automatic: When the corresponding domain name is under DDOS attack, it will automatically parse to high defense. Notify users after successful automatic configuration. It does not affect the current parsing status when the automatic switching condition is not triggered. 
Region: Different high defense parsing IPs can be configured according to the corresponding region, and the corresponding high defense IP can be purchased at [UDDOS](/uantiddos/uantiddos)  
High Defense IP: Users configure the corresponding high defense IP, which can read the previously created high defense IP or manually fill it in.

![](/images/monitor_gfjx3.png)

#### DDoS Configuration Synchronization

DDoS Configuration Synchronization: You can bulk copy the source domain configuration to the selected domains. Up to 50 can be copied in bulk.

!> Note:
(1) For domains with existing configurations, the new configuration will overwrite the old one.
(2) Configuration is not possible while in DDoS resolution status.
(3) Domains in DDoS configuration status cannot be configured.

DDoS Switch Confirmation: A second pop-up window confirms whether you need to perform bulk synchronization operations.
Synchronization Feedback: Feedback on synchronization results includes total synchronization information, number of successes, number of failures, and reasons for failure.

![](/images/monitor_gfjx4.png)
![](/images/monitor_gfjx5.png)

## Monitoring Settings

The monitoring settings here are for receiving and closing alert information at the domain level. Except for the automatic return to source setting for business exceptions, all are controlled by the global alert setting switch. If the corresponding switch of the global alert setting is not turned on, you will not be able to receive SMS or email alert notifications.

![](/images/monitor_set-get_settings.png)

The following switches are to turn on or off alerts or monitoring at the **domain level**.

### Attack Alert Monitoring

UWAF monitors the attack situation of the domain name, by default, if a single IP triggers the same type of attack more than 500 times within 1 minute, an alert email or SMS will be sent to the corresponding message subscription group users.

### Abnormal Status Code Monitoring

UWAF monitors the status code of the domain name business. The average QPS of the business needs to be greater than 10, and if it is less than 10, an alert will not be triggered. If the proportion of response codes above 499 in the overall request is greater than 30%, an alert email or SMS will be sent to the corresponding message subscription group users. The frequency is once every 5 minutes.

### Source Station Status Monitoring

By default, UWAF will use the HEAD request method to probe the added domain names. The probing path is: `Probing Client -> UWAF -> Source Station` or `Probing Client -> Source Station`. The availability of HTTP and HTTPS services represents the status of the former link. Please note whether the source station or domain name has a security policy. If so, the monitoring IP (return to source IP) of UWAF needs to be added to the whitelist. If there are 3 consecutive abnormal responses within 5 minutes, an alert email or SMS will be sent to the corresponding message subscription group users. The frequency is once every 5 minutes.

?> Note:  
After this function is turned off, it will no longer send alert emails or SMS, but the UWAF probing client will continue to probe the source station.  
The UWAF probing client will randomly select an address in the return source IP segment as the source IP for probing (in rare cases, the domain name protection IP will be used as the source IP). If the source station or domain name has a security policy, the source station needs to allow the HEAD request of UWAF's return source IP, and at the same time add the return source IP to the domain name whitelist in the UWAF console.

Users can also customize the probing request path. If a complete URL is filled in the monitoring address, the response of visiting this URL will be used as the basis for judging the status of the source station.

### Configuration Example

After we have custom set a source site status monitoring address,
![](/images/monitor_set-set_monitor_url.png)

Wait for a few minutes, the probe request received by the source server should be the custom set file path. The log is as follows:
![](/images/monitor_set-get_monitor_log.png)

### Automatic Return to Source Setting for Business Exceptions

After enabling the automatic return to source setting for business exceptions, UWAF will monitor the availability of the domain's business. Please note whether the source site or domain has a security policy. If so, the UWAF monitoring IP (return to source IP) needs to be added to the whitelist. If the response code of the source site probe request is greater than 499 for 10 consecutive times and the QPS of the business is greater than 50, then the DNS resolution address of the domain will be pointed to the source site of the domain (in the case of multiple source sites, the default is the first source site). The detection and monitoring principle of this function is the same as [source site status monitoring](#source site status monitoring). If a monitoring address has been customized, this URL will be probed. At the same time, you can manually perform [business return to source](#business return to source) or [release return to source](#release return to source) for the domain's resolution.
