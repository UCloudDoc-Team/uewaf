# 日志服务

## 日志查询

UWAF 控制台提供最大 1 万条的访问日志查询功能，具体路径为【功能设置】->【日志服务】->【日志查询】，可以查看访问请求的时间、源目 IP 地址、User-Agent、状态码等，访问日志不含 HTTP 请求中的 Body 内容。

![](/images/log-get_log.png)

展开搜索设置后，可添加过滤条件搜索特定的日志，支持以来源 IP，目标 IP, Referer, URL, User-Agent, 状态码等条件进行过滤，其中 Referer, URL, User-Agent 支持模糊搜索，可同时添加多个条件进行搜索。

![](/images/log-query_log.png)

## 日志下载

UWAF 提供访问日志和攻击日志的下载功能，默认支持支持 7 天的日志下载，开通日志扩展包后最大支持 180 天的日志下载。

日志使用 gzip 压缩后上传到 UWAF 的 US3 存储中（因日志大小、压缩操作、网络等因素，压缩包上传存在延时），一般情况下 1 小时压缩一次，日志量较多的情况会视日志大小缩短日志压缩周期，最短压缩周期 5 分钟。若某一时间段内没有日志产生，则不会生成该时段的日志压缩包。选择指定日志后的【下载】按钮，在弹窗中可得到已上传的日志压缩包，点击链接后即可下载。如浏览器未自动下载，请更换浏览器重试或复制链接后下载。

![](/images/log-download_log.png)

若需要批量下载日志，可使用 API 下载，相关 API 文档：[下载访问日志](/api/uewaf-api/download_waf_access_log)。