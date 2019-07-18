{{indexmenu_n>4}}

### UWAF 开启SNI服务

SNI（Server Name Indication）是HTTPS应用的一个扩展，用于一个IP上运行多个HTTPS服务，在SSL Handshake阶段发送ClientHello报文时附带上，通过抓包可以看到。
WAF为每个域名分配独立的防御IP，默认不要求客户端发送SNI。出于保密考虑（防止旁路系统抓取域名），WAF在回源时也不添加SNI扩展。如果源站有多个HTTPS服务时，可能会出现用户访问失败。
如果您的源站有多个HTTPS服务共有一个IP，请联系WAF技术支持开启SNI扩展功能。


