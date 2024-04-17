# Interception Page

!> Note:  
This feature requires the flagship version or above.

By default, when UWAF determines a request as an attack request, it will intercept the request at UWAF while recording the attack log, and return a default interception page with a response status code of 404 to the client. The custom interception page feature allows you to customize the response status code and page content of the interception page.

![](/images/intercept_page-get_rule.png)

The response status code of the interception page is set to 0 by default, i.e., the status code is 200, but it can also be customized to a status code between 200-599.

Click on [Edit Content], you can enter custom text or HTML code, so when the attack request is intercepted, the custom interception page will be displayed. If the page content is set, this feature is enabled by default. If the content is empty, this feature is in the off state. The page supports content parsing of HTML code and TXT plain text document formats.
