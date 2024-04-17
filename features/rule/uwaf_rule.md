# UWAF Rules

UWAF itself includes various types of default protection rules (protocol violations, injection attacks, cross-site scripts, vulnerability attacks, command execution, etc.). In addition to the rules already in these types, you can also customize and add protection rules to precisely intercept attacks and allow certain requests.

> For the priority of various rules, please refer to [Rule Priority](/uewaf/features/rule/mode?id=Rule Priority).

## Rule List

Rules have different priorities. The default rules are at the lowest priority and cannot adjust their priority, but you can choose to turn on or off the rule judgment of a certain type. The priority of custom rules can be adjusted. The rule at the top of the rule list has the highest priority, and the priority of the rules below decreases in turn.

- You can increase or decrease the priority of the rules. The priority of the rules above the list is higher than the rules below;
- If a rule with a higher priority conflicts with a rule with a lower priority, the rule with a higher priority will prevail;
- The priority of the system's default rules is the lowest and cannot be adjusted.

![](/images/uwaf_rule-get_rule.png)

## Add Rules

The rule consists of rule name, matching action, risk level, risk type, and matching conditions. In the blocking mode and alarm mode, if the matching action of the rule is to intercept, a request hitting a custom rule will record an attack log. The log details can be viewed in [Attack Details](/uewaf/features/report/attack_details); if the matching action of the rule is to allow, a request hitting this rule will not generate an attack log. **In the alarm mode, intercepting requests will only record attack logs, but will not block requests**.

![](/images/uwaf_rule-add_rule.png)

### Rule Parameter Description

| Parameter           | Description                                                  |
| ------------------- | ------------------------------------------------------------ |
| Rule Name           | The name of the custom rule, which can be any Chinese or English character |
| Matching Action     | Intercept or allow. Intercepting will record attack logs, and allowing will not record attack logs |
| Risk Level          | High risk, medium risk or low risk, used to identify the risk level of the rule |
| Risk Type           | Identifies the type of rule. Optional values: Malicious Scanning, Protocol Deformity, Unauthorized Access, Information Leakage, WebShell, Vulnerability Attack, Cross-Site Scripting, CC Attack, Injection Attack, Command Execution, Other Attacks |
| Matching Conditions | Composed of matching fields, logical symbols, matching content and parameter decoding. The logic between multiple conditions is and, that is, when all conditions are met, the rule can be hit. For detailed explanation, see [Matching Condition Description](/uewaf/features/rule/uwaf_rule?id=Matching Condition Description) at the bottom of the document |

### Matching Condition Description

The description of the matching fields and their corresponding logical operators are as follows:

| Matching Field         | Description                                                  | Logical Operator                                             |
| ---------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Source IP              | The source IP of the request client. If the [WAF has a proxy in front] is enabled, the IP of the specified field is taken as the source IP | Belongs to, does not belong to (CIDR format); equal to, not equal to |
| Referer                | When jumping between different web pages, the link address of the source page will be attached to tell the server which page it was linked from | Contains, does not contain; equal to, not equal to; length greater than, less than; does not exist; regex; multi-line, non-multi-line match |
| Request UA             | A string used to identify the request client, that is, the User-Agent field of the HTTP request | Contains, does not contain; equal to, not equal to; length greater than, less than; regex; multi-line, non-multi-line match |
| Request Path           | The client submits a request path to access the specified resource on the server, for example, the request path for the homepage is `/` | Contains, does not contain; equal to, not equal to; length greater than, less than; regex; multi-line, non-multi-line match |
| Request Method         | The method of the request, such as `GET`, `POST`             | Contains, does not contain; equal to, not equal to; length greater than, less than; regex; multi-line, non-multi-line match |
| Request Content        | The content of the Body part of the request                  | Contains, does not contain; equal to, not equal to; length greater than, less than; regex; multi-line, non-multi-line match |
| URL Query Parameter*   | Parameters in the URL, for example `?a=1&b=2`, then the URL query parameters are `a, b`, and the parameter values are `1, 2` | Contains, does not contain; equal to, not equal to; length greater than, less than; does not exist; regex; multi-line, non-multi-line match |
| Request Cookie*        | The Cookie of the client request, Cookie is used to record some web page configurations or to identify the identity to the server | Contains, does not contain; equal to, not equal to; length greater than, less than; does not exist; regex; multi-line, non-multi-line match |
| Request Parameter*     | Includes parameters in the URL, Cookie, and Body             | Contains, does not contain; equal to, not equal to; length greater than, less than; does not exist; regex; multi-line, non-multi-line match |
| Custom Request Header* | Other fields in the client request except Referer, User-Agent, Cookie, can also be custom fields | Contains, does not contain; equal to, not equal to; length greater than, less than; does not exist; regex; multi-line, non-multi-line match |

Fields marked with * indicate that they are key-value structures. The matching content of these fields can accept a JSON string to match the value, key name, value name or all keys, value names of a single key. **If you enter a normal string or a string that does not conform to the JSON format, it will match all key names and values by default**. If the operator corresponding to the key-value structure matching field is greater than/less than in length, and no **specific key value** is specified, the comparison is the total number of keys/values.

| Matching Content Type | Example Usage                                       | Description                                                  |
| --------------------- | --------------------------------------------------- | ------------------------------------------------------------ |
| Specific Key Value    | `{"pattern": "string", "specific": "specific-key"}` | Matches the value of a specific key `specific-key` in the key-value structure. For example: for custom request headers, check whether the value of the `specific-key` field in the request matches `string`; for URL query parameters, if it is `?specific-key=xxx`, check whether `xxx` matches `string` |
| All Key Names         | `{"pattern": "string", "keys": true}`               | Traverse and match all key names in the key-value structure. For example: the URL query parameter is `?a=1&b=2`, it will check whether the keys `a` and `b` match `string`, and any key match will trigger the rule |
| All Values            | `{"pattern": "string", "values": true}`             | Traverse and match all values in the key-value structure. For example: the URL query parameter is `?a=1&b=2`, it will check whether the values `1` and `2` match `string`, and any value match will trigger the rule |
| All Key Names, Values | `{"pattern": "string", "all": true}`                | Traverse and match all key names and values in the key-value structure. For example: for URL query parameters, if it is `?a=1&b=2`, it will check whether the key values `a`, `b`, `1` and `2` match `string`, and any key/value match will trigger the rule |
| All Key Names, Values | `string`                                            | Will be parsed as `{"pattern": "string", "all": true}`       |

### Parameter Decoding Explanation

Decoding can be performed on matched content, supporting multiple selections, including:

- URL decoding
- HTML decoding
- BASE64 decoding
- Remove comments  
  Remove `/*` and `*/` and the characters between them in the matched content
- Space compression  
  Compress multiple whitespace characters (including spaces) into a single space character

The source IP cannot be parameter decoded, if selected it will be ignored.

## Rule Examples

1. If the business domain `example.com` has 2 UWAF rules:

- Rule 1: If the request path contains `.php`, then intercept
- Rule 2: If the source IP contains `192.168.1.1`, then allow
  Rule 1 has a higher priority than Rule 2 (ordered).

Scenario (1): When the client's IP address is 192.168.1.1, if it sends a request with the URL `http://example.com/123.php`, it will trigger Rule 1 and be intercepted.  
Scenario (2): When the client's IP address is 192.168.1.1, if it sends a request with the URL `http://example.com/?i=<script>alert(/1/)</script>`, it will trigger Rule 2 and be allowed.

2. If the business domain `example.com` has a backend management login entrance `/admin.php`, it needs to use UWAF to configure source IP address access restrictions, and cannot completely open the rule detection for these source IP addresses.
   Rule example:

   - Rule name: Backend interface access restriction
   - Matching action: Intercept
   - Risk level: High risk
   - Risk type: Unauthorized access
   - Matching conditions:
     - Source IP does not belong to `12.34.5.0/24` (Allowed access IP or IP range)
     - Request path contains `/admin.php` (Backend management entrance)

   Scenario (1): When the client's IP address is 12.34.5.6, accessing `http://example.com/admin.php` will not trigger this rule, but will check for other subsequent rules.  
   Scenario (2): When the client's IP address is 65.43.2.1, accessing `http://example.com/admin.php` will trigger this rule and be intercepted.

3. If a certain business domain's technology stack has a component that has exposed a vulnerability, as long as the length of the value of the `jam` name in the request's Cookie is greater than 9, this vulnerability can be exploited (for example `jam=0123456789`, the length of the value is 10). Before the related patch is released, UWAF needs to be used to protect this vulnerability.
   Rule example:

   - Rule name: Protect cookie-jam vulnerability
   - Matching action: Intercept
   - Risk level: High risk
   - Risk type: Vulnerability attack
   - Matching condition: Request Cookies length greater than `{"specific": "jam", "pattern": "9"}`

   Scenario (1): When a normal client sends a request with the Cookie field value of `username=Alice;jam=true`, it will not trigger this rule, but will check for other subsequent rules.  
   Scenario (2): When a malicious client sends a request with the Cookie field value of `username=Mallory;jam=overflowattack`, it will trigger this rule and be intercepted.
