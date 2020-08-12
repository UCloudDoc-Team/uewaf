

# 日志服务
### 日志查询
![](/images/15971449150668.jpg)

UWAF 提供 在线流量日志1万条内的线上日志查看，用户可以在控制台查看这些请求内容，其中不包含BODY内的数据。

### 日志关键字查询
![](/images/15971449844658.jpg)

同时，用户可以根据搜索设置，对其中的来源IP，目标IP，refere, url, ua,状态码等条件进行模糊搜索，支持中文模糊匹配，支持多选。

### 日志下载
![](/images/15971450221047.jpg)
UWAF提供日常的流量日志与攻击日志的下载功能，会打包成压缩文件，以每小时为时间节点，进行文件上传，用户可以在UFILE进行下载这些文件。

### 日志结构
#### 流量日志结构说明
```
{
  "request_head": "HEAD / HTTP/1.1",  //请求方法、请求协议、路径
  "cookies": "",                      //cookies
  "upstream_status": "302",           //源站返回的响应码
  "@timestamp": "2020-04-21T00:06:27+08:00",    //请求时间
  "uri": "/",                           //被处理的URI
  "request_time": 0.048,                //完成请求的时间
  "remote_port": 40920,                 //转发到的源站监听的端口
  "hostname": "gd-waf-2",               //主机名
  "request_method": "HEAD",             //请求方法
  "server_port": 80,                    //请求的端口
  "forward": "",                        //XFF 字段
  "scheme": "http",                     //请求方法
  "status": "302",                      //WAF返回的响应状态码
  "request_length": 77,                 //请求的长度
  "upstream_response_length": "0",      //源站响应的长度
  "time": 1587398787.0,                 //请求的unix时间
  "host": "www.dns.dog",                //域名
  "referer": "",                        //Referer
  "content_type": "",                   //Content-type
  "request_uri": "/",                   //原始URI
  "remote_addr": "106.75.151.54",       //请求的IP
  "bytes_sent": 469,                    //请求的长度
  "top_id": 50146955,                   //公司ID
  "@source": "106.75.139.229",          //防御EIP
  "user_agent": "UWAF Domain State Monitor",     //UA内容
  "upstream_response_time": 0.048,          //源站响应时间
  "upstream_addr": "152.32.170.130:80"      //源站IP及端口
}
```
#### 攻击日志结构说明
```
{
    "hostname": "bj-waf-3",             //主机名
    "protocol": "http",                 //请求协议
    "servername": "test.com",           //域名
    "destip": "106.75.118.14",          //目标IP
    "id": "220.181.108.181-6bc4d18e",   //资源ID号
    "port": "80",                       //请求端口
    "alerts": [{"description": "XSS",   //拦截规则名
                "match": {"11": "s",    //命中规则的逻辑链
                         ......
                          "9": "a"},
                "id": 32006.0}],        //规则ID
    "client_ipinfo": {"iddcode": "86",  //攻击者IP信息
                     ......                      
                     "regionname": "\u5317\u4eac"},
    "request_headers": {"accept-language": "zh-cn,zh-tw",//请求头
                       ......
                       "fetchergroup": "TELECOM"},
    "attack": "xss",             //攻击类型
    "method": "GET",             //请求方法
    "falsepositive": false,      //标记误报
    "oid": 50100119.0,           //公司ID
    "timestamp": 1587317107,     //攻击时间
    "riskrank": "high",          //攻击风险
    "host": "shop.51ykb.com",    //域名
    "referer": "NULL",           //Referer
    "count": 1,                  //短时间内攻击次数
    "region": "cn-bj",           //地域
    "uri": "/javascript:history.back()",   //请求路径
    "client": "220.181.108.181",           //客户端IP
    "mode": "ACTIVE",                      //工作模式
    "action": "DENY",                      //触发动作
    "ua": "Mozilla/5.0 (compatible;        //请求头(Ua)
}
```
