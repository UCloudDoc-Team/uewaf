# CC 规则

?> CC防护开启后，会有一条默认规则生效，默认规则为单IP 1分钟内请求数不超过500次，此规则后端强制开启。如用户有自定义CC规则，则该条目不生效。

* 正常模式：仅自定义规则生效。
* 紧急模式：不仅自定义规则会生效，并且系统将根据数据分析、人工智能识别等技术对攻击进行拦截，可能存在误杀，开启后将根据攻击特点进行自动的拦截。并且会对请求加入cookie参数校验功能，如果应用具有301跳转功能，不建议开启紧急模式。

![](/images/15971389805368.jpg)

### 页面参数说明：自定义匹配条件

  - 时间：定义收集的时间，默认为10秒。即指在10秒内如果发现某个路径被访问了超过N次就会触发动作。
  - 路径：需要防护的网站地址。比如index.html
  - 次数：指访问的次数。
  - 动作：指满足条件后系统将会执行的动作。
  - 操作：编辑 或 删除

![](/images/15971391299486.jpg)

### 添加CC防护规则：参数说明

  - 时间：检测周期
  - 路径：完全匹配 为 等于条件，目标匹配 为 包含条件
  - 次数：次数限制
  - 动作：
     - 封禁该IP（iptables，如前面有CDN等代理，可能存在误封）
     - 拦截此类请求
     - 启用验证码（如用户验证通过，则会对该IP进行放白处理，时间等于规则配置时长）
  - 时长：生效周期

### 例子：
对网站开启全站CC防护功能，要求单IP每20秒不能超过50次请求。

#### 规则参考如下：
![](/images/15971393155084.jpg)

