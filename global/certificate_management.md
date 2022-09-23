# 证书管理

可以统一管理 UWAF 上的证书和 TLS 设置，包含了用户所有域名已上传的 SSL 证书，同时也支持配置 TLS 协议版本及加密套件（更改后**所有域名**的 TLS 版本和加密套件都会改变），也可以上传域名更新的证书替换掉将要到期的证书。

如果证书是在 USSL 购买的，UWAF 支持自动同步 USSL 的证书，用户在添加域名的时候，可以不用上传证书，UWAF 会自动拉取相关域名的证书。

![](/images/15971452268273.jpg)

## TLS 配置

可以全局设置 TLS 协议版本和加密套件，默认设置的 TLS 协议为 1.0, 1.1, 1.2 。加密套件预设强和中两个等级，也可以自定义加密套件，自定义的加密套件需要和协议版本匹配，可以使用 `openssl` 命令查询，如 ` openssl ciphers -tls1_1 -s` 查询 TLS 1.1 所支持的所有加密套件。

## 上传证书

证书文件需是 PEM(Privacy Enhanced Mail) 格式，这种证书文件格式的特点是：  
第一行以 `-----BEGIN ` 开头，最后一行以 `-----END ` 开头。若格式不正确会导致上传失败。

## 证书列表

证书列表包含如下参数：

- 证书名称：标识证书的名称，方便区分
- 所属域名：证书所属的域名
- 绑定域名：证书所绑定的域名
- 添加时间：证书上传到 UWAF 的时间
- 过期时间：证书的到期时间
- 操作：包含【绑定域名】和【删除】操作
  - 绑定域名：可以将证书绑定到勾选的域名
  - 删除：从 UWAF 上删除该证书