# Client's Real IP and Port

## UWAF Obtains the Real IP of Clients Accessing through Proxy Servers such as CDN

Normally, CDN will pass the real IP of the visiting user through XFF (X-Forwarded-For) or X-Real-IP. However, it does not rule out the situation where users construct this field to forge the request IP.

Taking UCDN as an example, if you want to get the real IP of the visiting user at the WAF end, you need to do the following:

1. Open the 'Domain Management' of the WEB application firewall console, select the domain name to be set, and click 'Edit'.
2. After opening, turn on the 'Is there a proxy before WAF' option, and fill in the X-Real-IP field in the 'Real IP Field Setting' (this field is the field where UCDN passes the user's real IP, if you choose other third-party proxies, please confirm the real IP field with the supplier).

![](/images/get_real_ip-set_xff.png)

3. After the configuration is completed, click 'OK' to let UWAF get the real IP of the client.

## Obtaining the Real IP of the Client from the Source Station

UWAF will add two fields, X-Real-IP and X-Forwarded-For, to the request header when returning to the source to transmit the real IP of the visiting user. The source server can make the corresponding [configuration](#Sample Configuration) to obtain the values of these two fields.

#### The Difference Between X-Real-IP and X-Forwarded-For

The proxy server (such as UWAF) will write the source IP of the request into the X-Real-IP field and then send it to the source station. This field will only have one IP address; however, with each level of proxy, the proxy server will append the source to X-Forwarded-For. In the case of multiple proxies, this field will have multiple IP addresses (real IP, proxy server 1, proxy server 2, ...).

## Obtaining the Real Port of the Client from the Source Station

UWAF will add the X-Real-Port field to the request header when returning to the source to transmit the real port of the visiting user. The source station can obtain the real port of the user client by taking the value of this header field.

## Sample Configuration

For common HTTP servers or web applications, the following methods can be used to obtain the real IP of the client:

#### Nginx

For Nginx servers, you can use `$http_x_real_ip` to get the value of the X-Real-IP field, and `$http_x_real_port` to get the value of the X-Real-Port field. Using the `http_realip_module` module of Nginx allows `$remote_addr` to display the real IP of the client. The added configuration is as follows:

```nginx
set_real_ip_from source IP segment; # The source IP segment can be viewed in the Basic Information section of the Overview page in the control panel. Multiple IP segments require multiple instructions.
real_ip_header X-Forwarded-For; # X-Real-IP can also be used
real_ip_recursive on; # If there are proxies like CDN in front of WAF, this instruction needs to be set to on, otherwise it is not needed.
```

If the source Nginx acts as a proxy server, in addition to the previous configuration, you can add the following content to the configuration so that the backend application can also obtain the real IP of the client through X-Real-IP or X-Forwarded-For:

```nginx
# ...
location / {
  # ...
  proxy_set_header Host $host;
  proxy_set_header X-Real-IP $remote_addr;
  proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
}
# ...
```

#### ASP

```c#
Request.ServerVariables("X-Real-IP")
```

#### JSP

```java
request.getHeader("X-Real-IP")
```

#### PHP

```php
$_SERVER["HTTP_X_FORWARDED_FOR"]
```

?> Note:  
If the upper link is a third-party proxy server such as CDN, it may not be possible to obtain the real IP. In this case, you need to refer to the previous article [WAF obtains the real IP of the client accessed through the CDN and other proxy servers](#uwaf-obtains-the-real-ip-of-the-client-accessed-through-the-cdn-and-other-proxy-servers) to enable the [Does WAF have a proxy in front] option in the domain settings in advance and specify the real IP field of the client.
