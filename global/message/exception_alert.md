# Abnormal Status Code Monitoring

UWAF monitors request traffic (the average QPS needs to be greater than 10, if it is lower than this average, this alert will not be triggered). If the proportion of status codes above 499 in the overall requests exceeds 30%, an alert email or SMS will be sent to the corresponding message subscription group users. The frequency is once every 5 minutes.

Abnormal status code alerts are generally triggered by the origin server returning a large number of status codes above 499. When the origin server does not respond for a long time, UWAF will return a 502 status code. This alert indicates that the network connection between UWAF and the origin server is open, but the origin server may not be able to process UWAF's back-to-source request in time. At this time, the situation of the origin server needs to be checked.

## Handling Abnormal Status Code Alerts

When you receive an email or SMS about an abnormal status code alert, please follow the steps below to check:

1. View the domain access situation in the "System Overview" of the "Security Report" to see if the access volume has surged, causing excessive pressure on the origin server.

2. Check whether the origin server is working normally, mainly whether the CPU usage rate and bandwidth usage rate are too high.

3. Check whether the origin server's IP is exposed. You can view the origin server logs to see if a large number of requests bypass WAF and directly access the origin server.

If you confirm that the origin server is normal but an alert is triggered, or if you think the alert is a false alarm, please consult technical support for help.
