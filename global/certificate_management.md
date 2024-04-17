# Certificate Management

You can centrally manage the certificates and TLS settings on UWAF, which includes all the SSL certificates uploaded for all user domains. It also supports the configuration of TLS protocol versions and encryption suites (changes will affect the TLS version and encryption suite of **all domains**). You can also upload updated domain certificates to replace those that are about to expire.

If the certificate is purchased from USSL, UWAF supports automatic synchronization of USSL's certificates. When users add a domain, they do not need to upload a certificate, as UWAF will automatically pull the relevant domain's certificate.

![](/images/certificate_management-get_certificate.png)

## TLS Configuration

You can globally set the TLS protocol version and encryption suite. The default TLS protocol is set to 1.0, 1.1, 1.2. If you choose protocol version 1.3, you must also choose 1.2, **you cannot choose 1.3 alone**. The encryption suite is preset to high and medium levels, but you can also customize the encryption suite. The **encryption suite you choose must match the protocol version**. You can use the `openssl` command to query the encryption suite corresponding to a certain protocol version, such as `openssl ciphers -tls1_1 -s` to query all encryption suites supported by TLS 1.1.

![](/images/certificate_management-set_tls.png)

## Upload Certificate

The certificate file needs to be in PEM (Privacy Enhanced Mail) format. The characteristics of this certificate file format are: 
The first line starts with `-----BEGIN `, and the last line starts with `-----END `. If the format is incorrect, the upload will fail.

## Certificate List

The certificate list contains all SSL/TLS certificates uploaded to UWAF, and also provides certificate binding and deletion operations.

### Parameter Description

| Parameter        | Description                                                  |
| ---------------- | ------------------------------------------------------------ |
| Certificate Name | The name identifying the certificate, for easy differentiation |
| Domain Ownership | The domain to which the certificate belongs                  |
| Bound Domain     | The domain to which the certificate is bound                 |
| Addition Time    | The time when the certificate was uploaded to UWAF           |
| Expiration Time  | The expiration time of the certificate                       |
| Operation        | Includes "Bind Domain" and "Delete" operations<br>● Bind Domain: You can bind the certificate to the selected domain<br>● Delete: Delete the certificate from UWAF |
