# Attack Overview

Choose the corresponding domain name or all domain names and the specified time range. The attack overview will display the preset attack analysis report according to the selected domain name and time range.

![](/images/attack_analysis-get_report_1.jpg)
![](/images/attack_analysis-get_report_2.jpg)

## Data Display

| Data Metrics                           | Description                                                  |
| -------------------------------------- | ------------------------------------------------------------ |
| Total Request Times                    | Total request count for the selected domain                  |
| Total Attack Times                     | Total attack count for the selected domain                   |
| Blacklist Interception Times           | The number of requests intercepted by the blacklist for the selected domain, i.e., the count of requests with a response status code of 444 |
| Custom Rule Trigger Times              | The number of requests that trigger custom rules for the selected domain |
| CC Rule Interception Times             | The number of times the CC rule is triggered for the selected domain. After the CC rule is triggered, subsequent requests may record a 444 status code |
| System Default Rule Interception Times | The number of requests that trigger the default UWAF rules for the selected domain |

## Chart Information Display

- Attack Time Protection Axis: Count the number of attacks allowed or intercepted over a period of time. If the selected working mode is "Record but do not intercept", then the protection behavior is "Allow". If the selected working mode is "Enable protection rules", then the protection behavior is "Intercept".
- Attack Classification Trend: Statistics of attack trends for different attack types
- Risk Level Distribution: Count the number of attacks at different risk levels.
- Attack Type Distribution: Count the number of attacks of different types.
- Top 10 Attack IPs: Which are the top 10 IPs with the most attacks (specific IPs can be excluded)
- Top 10 Attack Paths: What are the top 10 most attacked paths
- Top 10 Attack Source Locations: Where are the top 10 IPs initiating the most attacks from
- Top 10 Attack Request UAs: What are the top 10 request UA features initiating the most attacks
