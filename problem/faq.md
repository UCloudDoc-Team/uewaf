# Precautions & FAQ

## Precautions

- When the deployment area is in the domestic Beijing, Shanghai, and Guangzhou regions, the domain name must be registered.
- Domain Name System (DNS) service takes about 10 minutes to take effect, depending on the actual situation.
- Supports renewal, automatic renewal, change of billing method, version upgrade, and refund upon closure.
- Supports adding non-UCloud domain names, and you can choose any available zone to add. Currently, multiple regions are available for using UWAF (there is no difference in functionality or performance between the same versions in different available zones, only the configuration deployment data center locations are different).
- Downgrading of versions is not supported; if you need to delete the expansion pack purchased from the "Quota Management", you need to consult technical support.

## FAQ

### How to prevent attackers from bypassing UWAF?

The **source station** can configure a whitelist and blacklist, only allowing the UWAF back-to-source network segment and some trusted IP address segments, and rejecting connections from other IP addresses.

### How to view the UWAF back-to-source IP address?

In the UWAF console [overview](/uewaf/features/info/info?id=overview page description) interface, there is a column of "Basic Information" directly below the "Information Announcement" column. The last line is "Back-to-Source IP". Click "View" to get the corresponding back-to-source IP network segment address.

### Will UWAF support protection when the latest high-risk vulnerabilities appear?

Whenever the latest vulnerabilities burst out, our security engineers will follow up in real time, analyze the POC and vulnerability principles, extract the corresponding detection rules, and deploy new rules to UWAF in a timely manner.

### UWAF supports virtual patches, what is a virtual patch?

The UWAF system's blocking of vulnerability attacks is called a "virtual patch", which means it is not a real patching action, but a temporary blockage of attacks, buying time for the business side to update patches.

### If the source station is a ULB load balancing gateway, should I directly fill in the gateway IP or the subnet host IP?

If there is an external ULB, you can fill in the IP of the ULB gateway, and there is no need to fill in the subnet host IP. For request proxy type ULB, it is recommended to use [ULB version UWAF](/uewaf/use/ulb_with_uwaf), for available areas see [Price Description-ULB version UWAF](/uewaf/steer/price?id=ULB version UWAF).

### What should I pay attention to when enabling 【HTTP2 forwarding】 on the domain name on UWAF?

After enabling 【HTTP2 forwarding】, all domain names under the same protection IP will support HTTPS. If you only want to enable HTTP2.0 for individual domain names, it is recommended that such domain names use exclusive IP. For HTTPS 443 port, it is recommended to enable 【HTTPS redirection】 at the same time. HTTP port does not support HTTP2.0.

### What is the priority order of various rules on UWAF such as black and white lists, CC rules, and UWAF rules?

Refer to [Rule Priority](/uewaf/features/rule/mode?id=Rule Priority).

### What is the response status code of the request intercepted by UWAF?

For requests that trigger UWAF rules and are intercepted: respond with a 404 status code and the default interception page, flagship and exclusive customized users can customize the response status code and interception page of the interception.  
For requests from IPs that trigger CC rules: if the restriction method is to intercept such requests, refuse the connection and record a 444 status code; if the restriction method is to enable the captcha, respond with a 200 status code and the captcha page; if the restriction method is to limit the request rate, respond with a 429 status code for requests that exceed the rate.  
For requests from IPs on the blacklist, if the action is to intercept, refuse the connection and record a 444 status code; if the action is a captcha, respond with a 200 status code and the captcha page.
