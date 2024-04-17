# IP Query

The IP query function can query the basic information of a specified IP, as well as the request statistics of this IP visiting WAF during a specified period.

## Function Description

The function is divided into four parts as shown in the figure below:

- Query conditions (①, ②)
- IP information (③, ④, ⑤)
- IP operation (⑥)
- IP access trend (⑦)

![](/images/ip_query-get_data.png)

## Query Conditions

Choose the time range at ①, supporting the last 1 hour, 24 hours, and custom time (within 3 days) as time query conditions. Enter a single IP at ②, click on [Query] to query the basic information of this IP and the request statistics of visiting the current domain name during a specified period. If you want to query without distinguishing the domain name, please check [Global Search]. Checking this option can query the request statistics of this IP visiting all domain names.

## Query Conditions

At ①, select the time range. It supports the last 1 hour, 24 hours, and custom time (within 3 days) as time query conditions. At ②, enter a single IP, and click [Query] to query the basic information of this IP and the request statistics of visiting the current domain during the specified period. If you want to query without distinguishing the domain name, please check [Global Search]. Checking this option can query the request statistics of this IP visiting all domain names.

## IP Information

The IP information section displays the basic information of the IP (③), the current status of the IP (④), and an overview of the IP's behavior (⑤).

The basic information of the IP includes the location, positioning information, and operator information.

The current status of the IP explains whether this IP can normally access the current domain name, indicating whether the IP is blocked by the blacklist or CC rules or is allowed by the whitelist.

The IP behavior overview counts how many requests this IP has initiated during the queried period, the number of attacks, and how many times it has been intercepted.

## IP Operation

The IP operation section (⑥) can provide appropriate operation buttons based on the current status of the IP and the behavior overview.

If this IP is blocked by CC rules, you can unblock this IP; if there is an attack behavior, you can add it to the blacklist; if you need to allow access requests, you can add it to the whitelist; quickly and conveniently operate the queried IP.

## IP Access Trend

The IP access trend (⑦) has two parts, namely the number of IP response code requests and the number of IP attack category requests.

The first part, the number of IP response code requests, counts the response status code information of the queried IP during the specified period. You can understand the specific request situation of the IP according to the chart; the second part, the number of IP attack category requests, is the statistical information of the attack requests contained in the access of this IP. The chart can intuitively reflect the attack methods and trends of the IP. Checking the legend above the chart can accurately select the desired trend information.
