# HTTPS/Certificate Related Issues

## Enabling HTTPS Access

There are two ways:

1. Add a source station that supports the HTTPS protocol and upload the SSL certificate for the corresponding domain. If you need to redirect HTTP requests to HTTPS requests, please enable the [HTTPS Redirect] option, which only supports redirection from port 80 to port 443.
2. After adding a source station with port 443 for the HTTPS protocol, enable the [HTTP Back to Source] option, which only supports back to source from port 443 to port 80, and the source station needs to open port 80.

## Mobile Device HTTPS Access Abnormal

This problem usually occurs when mobile browsers (such as pre-installed browsers on Android systems, WeChat mini-programs) access HTTPS websites. The reason is that some mobile browsers will verify the website's SSL certificate and intermediate certificate. If the intermediate certificate is missing, the website cannot be accessed, and this type of access log cannot be found on UWAF.

### Solution

1. You can download the intermediate certificate from the certificate issuing authority, use a text editor or the `cat` command to append the content of the intermediate certificate after the content of the public key file, and upload the public key file that contains the intermediate certificate.
2. Complete the intermediate certificate through third-party tools (recommended to use `https://myssl.com/chain_download.html`) and download the certificate that contains the complete certificate chain, and then upload it.
3. Contact UCloud technical support to add the intermediate certificate in the background.

## SSL Certificate Format

UWAF supports PEM format certificates (which can be purchased through UCloud USSL and download the PEM format certificate file). Typically, PEM format certificates include two files. The file with a pem suffix is the public key file. After selecting the public key file, click the "Upload Public Key" button to upload. The file with a key suffix (the file suffix may also be pem, which can be distinguished by the file name) is the private key file. After selecting the private key file, click the "Upload Private Key" button to upload.

After the file is uploaded, UWAF will check the correctness of the certificate. If the check fails, an error will be returned and the certificate cannot be applied. Please troubleshoot according to the following steps and re-upload:

1. Whether the public key file and private key file are correct.
2. Whether the uploaded files are duplicated.
3. The certificate can be verified for correctness through third-party tools (recommended to use `https://myssl.com/match_key.html`).

If the SSL certificate is purchased from [USSL](/ussl/operate/buy) or hosted on [USSL](/ussl/operate/upload), UWAF supports automatic synchronization of such certificates.

## SSL Client Verification

UWAF supports HTTPS domain configuration client verification. If you have this requirement, please contact UCloud technical support. And please prepare the verification root certificate, CRT certificate.
