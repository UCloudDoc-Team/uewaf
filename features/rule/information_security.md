# Information Security Protection

UWAF rules are judgments made by UWAF after receiving requests, and information security protection rules are judgments made on the response received from the origin server after UWAF sends the request. Information security protection rules are controlled by the working mode and only take effect in **blocking mode**. Information security protection rules can filter out sensitive information in the response, disguise abnormal status codes and respond with custom content, and block specific content.

> For the priority of various rules, please refer to [Rule Priority](/uewaf/features/rule/mode?id=Rule Priority).

!> Note:  
The information security protection function currently only supports the judgment of response data of `text/plain` and `text/html` content types. That is, the value of the `Content-Type` field in the origin server response header is `text/plain` or `text/html`, and other content types are not supported.

### Rule Parameter Description

| Parameter           | Description                                                  |
| ------------------- | ------------------------------------------------------------ |
| Rule Name           | The name of the custom rule, which can be any Chinese or English character |
| Protection Type     | The type of information security protection rule, including [Sensitive Information Filtering](/uewaf/features/rule/information_security?id=Sensitive Information Filtering), [Response Code Security Control](/uewaf/features/rule/information_security?id=Response Code Security Control), [Custom Content Control](/uewaf/features/rule/information_security?id=Custom Content Control) |
| Information Content | You can select specific sensitive information, origin server response status code, and custom sensitive content |
| Match Action        | Information desensitization, response blocking or information disguise, response blocking |
| Content             | The content of the custom response, only effective when the match action is information disguise, supports txt plain text and HTML code |

?> Explanation:  
Blocking response means that the response content that triggers the rule will be blocked, and the connection of the request that triggers this rule will be disconnected, and the requesting client cannot obtain the blocked response content.  
Information disguise refers to replacing the response content of the origin server with custom content (txt plain text or HTML code).

## Sensitive Information Filtering

Perform sensitive information filtering on the response content of the origin server. If the content of the response can match the information content of the rule (ID number, mobile phone number, email, bank card number), these contents will be replaced with `*`.

![](/images/information_security-add_sensitive_rule.png)

## Response Code Security Control

Judge the response code of the origin server. If the response code can match the information content of the rule (the set status code between 400 - 599), the response will be blocked or the response of the origin server will be replaced to achieve information disguise according to the match action.

![](/images/information_security-add_status_rule.png)

## Custom Content Control

Judge the response content of the origin server. If the content of the response can match the information content of the rule, the response will be blocked.

![](/images/information_security-add_custom_rule.png)
