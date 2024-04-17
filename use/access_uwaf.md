# Accessing SaaS Version UWAF

The SaaS version of UWAF is a product that provides protection for business by being deployed in front of the Web server and forwarding proxies. By detecting the content of the traffic, it resists attacks such as SQL injection, XSS attacks, vulnerability attacks, and malicious scanning, ensuring the normal operation of the website.

Before accessing UWAF:
![](/images/access_uwaf-show_before_arch.jpg)

After accessing UWAF:
![](/images/access_uwaf-show_after_arch.jpg)

## Purchasing UWAF

Log in to the UCloud control panel, select UWAF from the product list: [All Products] -> [Security Protection] -> [WEB Application Firewall UWAF], and then click [Start Using] (if the service is not activated, please activate it first).

![](/images/purchase_waf-purchase_ui.png)""".

### Parameter Description

| Parameter                                                    | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Type                                                         | The type of area where UWAF is deployed, including mainland China, Hong Kong, Macao and Taiwan, overseas areas and ULB special zones |
| Region                                                       | The working area where the domain configuration is generated |
| Version Type                                                 | Different versions of UWAF, for detailed version differences, function and performance comparison, please check [Version Selection](/uewaf/steer/version_selection) |
| Extended Bandwidth                                           | When the bandwidth quota provided by the version does not meet the business needs, additional bandwidth expansion can be provided |
| Domain Extension Package                                     | When the number of domains provided by the version does not meet the business needs, additional domain extensions can be provided |
| [Exclusive IP](/uewaf/features/domain/domain_set?id=exclusive-ip) Points | This IP points can allocate an exclusive protection IP for the user's domain, and additional points can be provided in addition to the version quota |
| Log Extension Package                                        | Provides 180 days of log storage and download services, meets the requirements of equal protection, and the flagship version and above give away log extension packages |
| Advanced Features                                            | Advanced features beyond basic Web protection functions, for specific instructions, please check [Feature Description](/uewaf/steer/version_selection?id=Feature Description) |
| IPv6                                                         | IPV6 extension package, after opening, when adding a domain name, it can be additionally deployed to the IPv6 area to provide IPv6 access |
| Customized Requirements                                      | Some functions that cannot be adjusted on the console can be adjusted as needed, please consult technical support for details |

After purchasing the appropriate UWAF, you can follow the steps below to connect your business to UWAF.

## Add Domain

1. Click on [Domain Management] -> [Add Domain]
2. Fill in the domain and corresponding domain source address in the pop-up window. The domain can be a wildcard domain or a complete subdomain. After clicking [Confirm], get the generated CNAME information on the interface. After adding the domain, you can click [Edit] behind the corresponding domain in [Domain Management] to change the domain  
   ![](/images/domain_set-add_domain.png)

3. Domain Information Display  
   ![](/images/domain_set-get_domain.png)

4. For HTTPS sites, you need to upload the site's SSL certificate. If the certificate is purchased from [USSL](/ussl/operate/buy) or the certificate is hosted on [USSL](/ussl/operate/upload), the certificate of the corresponding domain will be automatically pulled when adding an HTTPS site.  
   ![](/images/access_uwaf-set_https.png)

Explanation of each domain configuration can be found [here](/uewaf/features/domian/domain_set.md?id=parameter-1).

!> Note:  
The domain must be already filed, unfiled domains cannot be added. Hong Kong, Macao, Taiwan and overseas regions are not subject to filing restrictions.

## Local Testing

1. Use the ping command to get the IP address corresponding to the CNAME protection domain
2. Open the hosts file, modify the client's hosts record, and point the site domain to the IP address obtained in step 1)  
   ![](/images/access_uwaf-ping_cname.jpeg)

?> Explanation:  
Windows system hosts file path: `c:\windows\system32\drivers\etc\hosts`  
macOS system hosts file path: `/private/etc/hosts`  
Linux system hosts file path: `/etc/hosts`

## Modify DNS Records

After obtaining the CNAME value for the corresponding domain name, you need to add a CNAME record at the DNS service provider to correctly resolve the site's domain name to the CNAME protection domain name provided by UWAF. If you are using the resolution service provided by DNSPod, you can add a CNAME record to the DNSPod control panel, as shown in the figure below.
![](/images/access_uwaf-set_hosts.jpeg)

### Test Whether the Configuration is Correct

To verify whether the CNAME resolution is complete, follow the steps below:

1. In the Windows operating system, use the shortcut `WIN + R`, enter `cmd` in the pop-up box and press enter; open any terminal in Linux or macOS.
2. Execute the command `nslookup -querytype=cname xxxxxx.uewaf.com`
3. If the command execution result shows the configured CNAME protection domain name or the IP obtained by resolving the CNAME protection domain name, it means the configuration is successful.

## Mode Selection

After the user has configured the DNS resolution, it is necessary to check whether the domain name is already in blocking mode. If not, you need to select the working mode of the domain name as blocking mode in [Protection Settings]. Start the protection function of UWAF.
