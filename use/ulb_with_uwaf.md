# Accessing ULB Version UWAF

After using the [ULB (Request Proxy Type)](https://docs.ucloud.cn/ulb/intro/architecture?id=%e5%a4%96%e7%bd%91ulb7) service, users can directly bind the Web Application Firewall (UWAF) to achieve secure protection of layer 7 HTTP/HTTPS services, while improving business availability and resource utilization.

The ULB version of UWAF provides web security protection capabilities on the layer 7 forwarding ability provided by ULB. Compared to the non-ULB version of UWAF, it does not have **external source station, view CC blocking IP, interception page, web page anti-tampering** functions. Other functions can refer to the UWAF Enterprise Edition, for specific information please refer to [Version Selection - Function Comparison](/uewaf/steer/version_selection?id=功能说明).

You can [bind ULB resources when purchasing UWAF](/uewaf/use/ulb_with_uwaf?id=购买UWAF时绑定ULB资源), and at least 1 ULB needs to be bound. If multiple ULBs are bound, cumulative billing is adopted, and the version quota will also accumulate. For example, if 2 ULBs are bound, it will cost 7300 yuan/month, supporting a total of 40 domains, and other quotas will also double.

After successful purchase and domain name access to UWAF, daily use is largely consistent with the non-ULB version of WAF, but forwarding functions such as bandwidth and ports need to be adjusted in the Basic Network UNet console or Load Balancing ULB console.

If the **ULB already exists and has been accessed by the business**, that is, to add WAF protection capabilities to the existing request proxy type load balancing, [you can start from this step](/uewaf/use/ulb_with_uwaf?id=anchor).

### Precautions

1. The available zones currently supported by the ULB Special Edition can be found in the [Pricing Description](/uewaf/steer/price?id=ULB版UWAF).
2. The domain name, origin server, bandwidth, port, SSL certificate, HTTP2.0, and IPv6 configuration of the ULB version of UWAF cannot be adjusted in the UWAF console. If adjustments are needed, please go to the UNet console for bandwidth and IPv6 configuration, and to the ULB console for other configurations.
3. The QPS metrics of the ULB version of UWAF can be found in the [Performance Metrics](https://docs.ucloud.cn/ulb/intro/performance) of ULB.

## Purchasing ULB Version WAF

### Binding ULB Resources When Purchasing UWAF

Users can select [Web Application Firewall UWAF] in [All Products], click [Start Using], and choose [ULB Special Edition] to purchase on the UWAF purchase interface.

**Please purchase 1 ULB resource first, otherwise, you will not be able to successfully purchase the ULB version of WAF**. If you have already purchased ULB services, you can see the configured ULB services in the drop-down menu under **Bind ULB Resources**, select the ULB resource you need to add, bind this resource, and then choose the domain name or log expansion package according to business needs and click [Buy Now].

![](/images/ulb_with_uwaf-purchase_waf.png)

The ULB Special Edition UWAF provides a default quota of 20 domain names. One domain name expansion package can add 10 domain name configurations; the log service provides log storage and download within 7 days by default, and the log expansion package service supports up to 180 days of log storage and download. Expansion packages are billed monthly.

## Connect to ULB Version UWAF

### Load Balancing Configuration

In the ULB console's [Load Balancing Management] interface, select the ULB resource that has bound UWAF, click [Details] in the operation column to operate, there are three steps:

1. Select [VServer Management], and click [Add VServer], fill in the VServer name and protocol and port, click [OK] to confirm, for detailed instructions, please refer to the ULB document: [Add VServer](https://docs.ucloud.cn/ulb/guide/vserver/createvserver)
   ![](/images/ulb_with_uwaf-add_verser_1.png)
   ![](/images/ulb_with_uwaf-add_verser_2.png)
2. In the [VServer Management] page, select [Service Node], click [Add Node], add the hosts listed in the optional resources on the left to the right as needed, click [OK] to confirm, for detailed instructions, please refer to the ULB document: [Add Service Node](https://docs.ucloud.cn/ulb/guide/realserver/addrealserver)
   ![](/images/ulb_with_uwaf-add_verser_3.png)
   ![](/images/ulb_with_uwaf-add_verser_4.png)

<div id='anchor'></div>

3. In the [VServer Management] page, select [Content Forwarding], click [Add Rule], choose [Domain] for forwarding rules, and select [Wildcard Resolution] from the drop-down box on the right, then fill in the domain to be protected (**UWAF does not support PCRE regular expressions, please be sure to select [Wildcard Resolution]**), add the resources listed in the optional nodes on the left to the forwarding nodes on the right as needed, click [OK] to confirm, for detailed instructions, please refer to the ULB document: [Add Content Forwarding Rule](https://docs.ucloud.cn/ulb/guide/forwardpolicy/addrule)
   ![](/images/ulb_with_uwaf-add_context_forward_1.png)
   ![](/images/ulb_with_uwaf-add_context_forward_2.png)

!> Note:  
Because ULB does not have malicious resolution protection, all requests will be forwarded to the source station by default, which may affect your normal business. Considering your Web application security, we strongly recommend that you follow the steps below to turn off the default full forwarding function of ULB.  
(1) In the [VServer] interface, select [Content Forwarding], then select the [Default] forwarding rule, click [Manage]  
(2) Select the forwarding node on the right, click the left button in the middle to delete this node  
(3) Repeat (2) until all nodes are deleted, then click [OK] to turn off the default full forwarding function of ULB  
After closing, if the user accesses a domain name not in the forwarding rule through ULB, a 502 error status code will be returned.  
![](/images/ulb_with_uwaf-unset_default_forward_1.png)
![](/images/ulb_with_uwaf-unset_default_forward_2.png)

### UWAF Configuration

In the UWAF console, click on 'Add Domain' in the 'Domain Management' interface. In the pop-up configuration interface, you can see the bound ULB resources. Drop down the domain and select the domain that needs to be added for protection. If there are proxy servers such as CDN, high defense, etc., in front of the ULB, you need to enable the 'Does WAF have a proxy in front' option and configure the correct proxy header. Then click 'OK' to add the domain. After that, accessing this domain through ULB will get security protection capabilities. For security protection configuration, please refer to the non-ULB version of UWAF.

![](/images/ulb_with_uwaf-add_domain_1.png)
![](/images/ulb_with_uwaf-add_domain_2.png)

### Modify DNS Resolution

If your business has been resolved to the ULB, you do not need to modify the DNS resolution record.

If your business has not yet been resolved to the ULB, you need to add the corresponding domain's A record at the DNS service provider of the domain. The record value should be the IP address of the basic network bound to the ULB.

## Unbinding and Deletion

If you want to unbind the UWAF from the ULB, just select the corresponding ULB resource on the 'Load Balancing Management' page of the ULB console, click on 'Details' and then select 'External Firewall' to unbind the corresponding Web Application Firewall.

To delete the ULB version of UWAF, you need to delete all domains on the 'Domain Management' page of the UWAF console, and then click 'Close UWAF' on the 'Overview' page to delete UWAF. After deducting the prorated cost of the used time, the remaining cost will be automatically returned within 1 hour.
