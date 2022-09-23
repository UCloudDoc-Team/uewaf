# UWAF 日志格式

UWAF 的访问日志与攻击日志均为 JSON 格式。攻击日志下载后可以指定字段提取相应的信息进行日志分析或接入专用的日志服务。

## 访问日志字段说明

| 字段                     | 说明                                         |
| ------------------------ | -------------------------------------------- |
| @timestamp               | 请求的时间，UTC 时间                         |
| bytes_sent               | 响应内容的大小，单位：字节                   |
| content_type             | 响应内容的类型                               |
| cookies                  | 请求的 Cookie 字段                           |
| forward                  | 请求的 X-Forwared-For 字段                   |
| host                     | 请求的 Host 字段，即域名                     |
| hostname                 | UWAF 主机名                                  |
| organization_id          | 项目 ID                                      |
| referer                  | 请求的 Referer 字段                          |
| region                   | UWAF 部署地域                                |
| remote_addr              | 来源 IP                                      |
| remote_port              | 来源端口                                     |
| request_id               | 请求唯一的 ID                                |
| request_length           | 请求内容的大小，单位：字节                   |
| request_method           | 请求方法                                     |
| request_time             | 响应时间，单位：秒                           |
| request_uri              | 请求的 URI                                   |
| scheme                   | 请求的协议                                   |
| server_addr              | 防护域名的 IP 地址                           |
| server_name              | 防护域名                                     |
| server_port              | 防护域名的端口                               |
| server_protocol          | 请求的 HTTP 协议版本                         |
| status                   | 响应状态码                                   |
| time_local               | 请求的时间，本地时间                         |
| top_organization_id      | 客户 ID                                      |
| upstream_addr            | 源站服务器地址                               |
| upstream_bytes_received  | 从源站接送的内容大小，类型：数组，单位：字节 |
| upstream_bytes_sent      | 传输给源站的内容大小，类型：数组，单位：字节 |
| upstream_response_length | 源站响应的内容大小，类型：数组，单位：字节   |
| upstream_response_time   | 源站响应的时间，类型：数组，单位：秒         |
| upstream_status          | 源站的响应状态码                             |
| uri                      | 请求实际被处理的 URI                         |
| user_agent               | 请求的 User-Agent 字段                       |
| x_real_ip                | 请求的 X-Real-IP 字段                        |

## 攻击日志字段说明

| 字段           | 说明                                     |
| -------------- | ---------------------------------------- |
| AccessId       | 攻击日志唯一的 ID                        |
| Action         | 规则的匹配动作，并非实际动作             |
| Alerts         | 触发的规则信息，类型：键值对数组         |
| Args           | 请求的 URI 中参数部分                    |
| Attack         | 攻击类型                                 |
| Client         | 来源 IP                                  |
| ClientIPInfo   | 来源 IP 的地理信息，类型：对象           |
| ClientPort     | 来源端口                                 |
| Count          | 攻击次数                                 |
| DestIp         | 防护域名的 IP 地址                       |
| FalsePositive  | 是否误报                                 |
| Host           | 攻击请求的 Host 字段，即域名             |
| Id             | 攻击日志唯一的 ID                        |
| Method         | 攻击请求的请求方法                       |
| Mode           | UWAF 防护模式                            |
| Port           | 防护域名的端口                           |
| Protocol       | 攻击请求的 HTTP 版本                     |
| Referer        | 攻击请求的 Referer 字段                  |
| Region         | UWAF 部署区域                            |
| RequestBody    | 攻击请求的 Body 内容，截取 512 字节      |
| RequestHeaders | 攻击请求的所有请求字段，类型：键值对数组 |
| RequestID      | 请求唯一的 ID                            |
| RiskRank       | 风险等级                                 |
| ServerName     | 防护域名                                 |
| TimeStamp      | 攻击发生的时间，秒级时间戳               |
| TopId          | 客户 ID                                  |
| UA             | 攻击请求的 User-Agent 字段               |
| Uri            | 攻击请求的 URI                           |
