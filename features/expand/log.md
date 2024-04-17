# Log Service

## Log Query

The UWAF console provides a maximum of 10,000 access log query functions. The specific path is [Function Settings] -> [Log Service] -> [Log Query]. You can view the time of access requests, source and destination IP addresses, User-Agent, status codes, etc. The access log does not contain the Body content in the HTTP request.

![](/images/log-get_log.png)

After expanding the search settings, you can add filter conditions to search for specific logs. It supports filtering by source IP, destination IP, Referer, URL, User-Agent, status codes, etc. Among them, Referer, URL, User-Agent support fuzzy search, and multiple conditions can be added for search at the same time.

![](/images/log-query_log.png)

## Log Download

UWAF provides the function of downloading access logs and attack logs. By default, it supports downloading logs for 7 days. After opening the log extension package, it supports downloading logs for up to 180 days.

The logs are compressed using gzip and uploaded to UWAF's US3 storage (due to log size, compression operation, network and other factors, there is a delay in uploading the compressed package). Generally, it is compressed once every hour. If there are a lot of logs, the log compression cycle will be shortened according to the log size, with the shortest compression cycle being 5 minutes. If no logs are generated during a certain period, the log compression package for that period will not be generated. After selecting the specified log, click the [Download] button, and you can get the uploaded log compression package in the pop-up window. Click the link to download. If the browser does not automatically download, please change the browser to try again or copy the link to download.

![](/images/log-download_log.png)

If you need to download logs in batches, you can use the API to download. Related API documentation: [Download Access Log](/api/uewaf-api/download_waf_access_log).
