<div id="黑名单"></div>

# 黑名单（全局）

此黑名单为全局黑名单，不同于[域名黑名单](/uewaf/features/expand/black_list)，全局黑名单对所有域名生效。全局黑名单的匹配动作只支持拦截，不支持验证码，也不支持指定有效时间。

可以自定义添加需要拉黑的 IP 地址，支持单个 IP 地址、IP 地址段、IP 网段（CIDR 格式）。也可以快速的重置全局黑名单，即将全局黑名单内的规则全部删除。

![](/images/white_list-get_global_rule.png)

> 各类规则的优先级参见[规则优先级](/uewaf/features/rule/mode?id=规则优先级)。
