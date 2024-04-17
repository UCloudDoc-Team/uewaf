# Anti-DDos Service Combined with UWAF

?> Note:  
Based on SaaS version UWAF.

UCloud's Anti-DDos Service and Web Application Firewall (UWAF) are fully compatible.

## Deployment Architecture

![](/images/ddos_with_uwaf-show_arch.jpeg)

## Purchasing UWAF

Log in to the UCloud console, select UWAF from the product list: [All Products] -> [Security Protection] -> [WEB Application Firewall UWAF], then click [Start Using] (if the service is not activated, please activate it first).

## Adding a Domain Name

In the [Domain Management] tab of the UWAF console, click [Add Domain Name]. In the pop-up window, fill in the site domain name, source IP, and other information. The domain name can be a wildcard domain or a complete subdomain. After clicking [OK], obtain the generated CNAME information from the interface.

!> Attention:  
The domain name must be already registered, unregistered domain names cannot be added. There are no registration restrictions for Hong Kong, Macau, Taiwan, and overseas regions.
If the site to be protected is an HTTPS site, you need to upload the site's SSL certificate. If the certificate is purchased from [USSL](/ussl/operate/buy) or the certificate is hosted on [USSL](/ussl/operate/upload), the certificate for the corresponding domain name will be automatically pulled when adding an HTTPS site.

## Domain Name Test

PING CNAME protected domain to get the assigned IP of UWAF

## Modify the IP of the High Defense Source Station

1. Configure the Anti-DDoS, fill in the IP of the UWAF obtained just now for the source station IP
2. After clicking OK, a CNAME address for Anti-DDoS will be generated
3. For subsequent DNS configuration, resolve the domain name that needs to be protected to the Anti-DDoS CNAME to complete the configuration""".
