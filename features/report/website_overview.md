# System Overview

The system overview will display the current running status of your website, including the number of requests, QPS, response codes, response time, traffic trends, etc. for each domain.

## Data Display

| Data Metrics                 | Description                                                  |
| ---------------------------- | ------------------------------------------------------------ |
| Total Request Count          | Total request count for the selected domain                  |
| Number of Request Source IPs | Count of different IP addresses in the requests for the selected domain. If there is a proxy server in front, this data may be inaccurate |
| Request Source Region        | Count of all source IP addresses' geographical region affiliation in the requests for the selected domain |

![](/images/website_overview-get_report_1.jpg)
![](/images/website_overview-get_report_2.jpg)

![](/images/website_overview-get_report_3.png)

In the "Top 10 Request IPs", you can click on the "Ignore" next to the count to exclude this IP from the Top 10. Up to 10 IPs can be excluded. The excluded IPs will be displayed at the top of this section. Users can click on the 'x' next to the corresponding IP to cancel the ignore, as shown in the figure below.

![](/images/website_overview-get_report_4.png)

## Chart Information Display

Domain categories:

- Request Trend: Request trend of categorized domains
- QPS Trend: QPS request situation
- Response Code: Response distribution of categorized domains
- Response Time: Average response time
- Upstream Traffic: User upstream traffic request trend
- Downstream Traffic: User downstream traffic request trend
- TOP 10 Request IPs: The 10 IPs with the most requests (if there is a third-party proxy, this data may be inaccurate)
- TOP 10 Request URLs: The 10 most visited paths
- TOP 10 Request Regions: The regions with the most requests based on IP source affiliation
- TOP 10 Request UAs: The UAs with the most requests
