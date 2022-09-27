# 告警设置

告警设置包含了全局的通知对象设置及开关等，共四种类型：安全报告、攻击告警监控、源站状态监控、异常状态码监控。

![](/images/alert-get_status.png)

## 安全报告

统计用户全部域名在固定时间周期内的安全攻击报告，通过勾选的通知方式对应通知对象。**没有攻击则不会生成安全报告**。

## 攻击告警监控/源站状态监控/异常状态码监控

详情说明请点击对应的链接：

- [攻击告警监控](/uewaf/features/domain/monitor_set?id=攻击告警监控)
- [源站状态监控](/uewaf/features/domain/monitor_set?id=攻击告警监控)
- [异常状态码监控](/uewaf/features/domain/monitor_set?id=异常状态码监控)

## 关闭告警

将最后一列的开启状态置为 OFF 即可关闭对应类型的全局告警。域名级别的关闭需在【[域名管理](/uewaf/features/domain/domain_set)】中找到指定的域名条目，点击【更多】后再点击【[监控设置](/uewaf/features/domain/monitor_set?id=监控设置)】，在弹出的界面中选择开启或关闭对应域名的相关告警功能。
