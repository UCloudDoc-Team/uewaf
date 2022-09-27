# 功能描述

UCloud Web 应用防火墙（UWAF）用于防护来自内外部的针对网站应用的安全威胁。与高防服务（UDDoS）兼容，除高防服务提供的防护外，还可以防护网络上常见的注入，命令执行，CC 等网络攻击。

## 基本概念

企业级 WEB 应用防护墙是部署在源站服务器之前，购买后将 UWAF 提供的 CNAME 配置到域名的 CNAME 解析中，然后所有的公网流量都将经过 UWAF，恶意的攻击流量将会被过滤，正常的流量才可以通过 UWAF 传送到源站服务器，从而保证源站服务器的安全。

## Web 应用攻击防护

全面防护以下攻击类型：SQL 注入、XSS 跨站、WebShell、命令注入、非法 HTTP 协议请求、常见 Web 服务器漏洞攻击、核心文件非授权访问、路径穿越等。提供后门隔离保护及扫描防护等功能。

## 精准访问控制规则

- 提供友好的配置控制台界面，支持 IP、URL、Referer、User-Agent 等 HTTP 常见字段的条件组合，打造强大的精准访问控制策略，可支持盗链、网站后台保护等防护场景。
- 与 Web 常见攻击防护、CC 防护等安全模块采用联动机制，打造多层综合保护机制、可根据需求，识别可信与恶意流量。

## 恶意 CC 攻击防护

- 对单一源 IP 的访问频率进行控制，支持重定向跳转验证、及人机识别等。
- 针对海量慢速请求攻击，根据统计响应码及 URL 请求分布、异常 Referer 及 User-Agent 特征识别，结合网站精准访问控制进行综合防护。

## 丰富报表

提供丰富的攻击与访问报表，让您及时了解网站状况。

## 黑白名单

- 黑名单：拦截指定的 IP 或 IP 段。
- 白名单：放行指定的 IP 或 IP 段。

## 日志查询与下载

- UWAF 支持实时查询 3 天内，在线 1 万条的日志查询。提供 7 天内的日志下载（攻击日志与访问日志）。
- 如用户开启日志扩展包服务之后，则支持最大 180 天的日志下载服务（旗舰版以上用户免费使用）。

## 告警管理

- 定时发送 UWAF 相关域名的告警汇总信息，发送至用户邮箱，提醒发生的风险。
- 实时发送 UWAF 相关域名短时间内触发大量规则的告警，发送告警至用户邮箱或手机，提醒发生安全事件的风险。
- 实时发送 UWAF 相关域名源站不正常响应的告警，发送至用户邮箱，提醒用户检查源站。
- 实时发送 UWAF 相关域名请求响应状态，如整体请求中 499 以上状态码比例大于 30%。则会发送告警至用户邮箱或手机。