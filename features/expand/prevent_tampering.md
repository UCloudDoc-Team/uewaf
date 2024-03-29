# 网页防篡改

网页防篡改功能可以在源站某些网页文件被恶意篡改后，但 UWAF 侧返回的网页不被篡改。原理为添加规则后，第一次访问规则中的 URL 时，UWAF 会缓存该 URL 对应的静态网页文件，第二次访问该 URL 就不会请求源站了，网页有更新时需要手动更新缓存。

![](/images/prevent_tampering-get_rule.png)

!> 注意：  
添加的 URL 域名必须与顶部域名选择框内选择的域名一致。

## 添加规则

可以针对 URL 添加防篡改规则。

### 参数说明

| 参数     | 说明                                                                        |
| -------- | --------------------------------------------------------------------------- |
| 业务名称 | 规则名称                                                                    |
| URL      | 需要保护的静态网页文件地址，需要填写 html 或者 htm 的**静态文件**的完整链接 |
| 状态     | 单独控制某一条放篡改规则的状态，可以【开启防护】或者【关闭防护】            |

例如：要针对 `https://example.com/some_activities.html` 这个 URL 的静态网页文件开启网页放篡改，如下图所示添加规则：

![](/images/prevent_tampering-add_rule.png)

## 全局防篡改开关

【添加规则】旁的【网页防篡改】开关为控制网页放篡改的全局开关，关闭时所有的防篡改规则均不生效，开启时防篡改规则由其自身的防护状态决定

## 备注

1. 如何更改【防护状态】？  
   可以点击相应规则一栏后方的【编辑】按钮后，在弹出的规则编辑框中完成

2. 【更新缓存】有什么用？  
   当你的网页做了修改，更新缓存可以清除 UWAF 侧的缓存
