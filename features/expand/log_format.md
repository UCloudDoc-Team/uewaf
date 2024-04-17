# UWAF Log Format

The access logs and attack logs of UWAF are both in JSON format. After downloading the attack logs, you can specify fields to extract relevant information for log analysis or access to dedicated log services.

## Access Log Field Description

| Field                    | Description                                                 |
| ------------------------ | ----------------------------------------------------------- |
| @timestamp               | Request time, UTC time                                      |
| bytes_sent               | Size of response content, in bytes                          |
| content_type             | Type of response content                                    |
| cookies                  | Request's Cookie field                                      |
| forward                  | Request's X-Forwared-For field                              |
| host                     | Request's Host field, i.e., domain name                     |
| hostname                 | UWAF hostname                                               |
| organization_id          | Project ID                                                  |
| referer                  | Request's Referer field                                     |
| region                   | UWAF deployment region                                      |
| remote_addr              | Source IP                                                   |
| remote_port              | Source port                                                 |
| request_id               | Unique ID of the request                                    |
| request_length           | Size of request content, in bytes                           |
| request_method           | Request method                                              |
| request_time             | Response time, in seconds                                   |
| request_uri              | Request's URI                                               |
| scheme                   | Request's protocol                                          |
| server_addr              | IP address of the protected domain                          |
| server_name              | Protected domain                                            |
| server_port              | Port of the protected domain                                |
| server_protocol          | Version of the request's HTTP protocol                      |
| status                   | Response status code                                        |
| time_local               | Request time, local time                                    |
| top_organization_id      | Customer ID                                                 |
| upstream_addr            | Source server address                                       |
| upstream_bytes_received  | Size of content received from source, type: array, in bytes |
| upstream_bytes_sent      | Size of content sent to source, type: array, in bytes       |
| upstream_response_length | Size of source response content, type: array, in bytes      |
| upstream_response_time   | Time of source response, type: array, in seconds            |
| upstream_status          | Response status code of the source                          |
| uri                      | URI that the request actually processed                     |
| user_agent               | Request's User-Agent field                                  |
| x_real_ip                | Request's X-Real-IP field                                   |

## Attack Log Field Description

| Field          | Description                                                  |
| -------------- | ------------------------------------------------------------ |
| AccessId       | Unique ID of the attack log                                  |
| Action         | Matching action of the rule, not the actual action           |
| Alerts         | Triggered rule information, type: key-value pair array       |
| Args           | Parameter part in the request's URI                          |
| Attack         | Attack type                                                  |
| Client         | Source IP                                                    |
| ClientIPinfo   | Geographical information of the source IP, type: object      |
| ClientPort     | Source port                                                  |
| Count          | Number of attacks                                            |
| DestIp         | IP address of the protected domain                           |
| FalsePositive  | Whether it is a false positive                               |
| Host           | Host field of the attack request, i.e., domain name          |
| Id             | Unique ID of the attack log                                  |
| Method         | Request method of the attack request                         |
| mode           | UWAF protection mode                                         |
| Port           | Port of the protected domain                                 |
| Protocol       | HTTP version of the attack request                           |
| Referer        | Referer field of the attack request                          |
| Region         | UWAF deployment region                                       |
| RequestBody    | Body content of the attack request, cut off at 512 bytes     |
| RequestHeaders | All request fields of the attack request, type: key-value pair array |
| RequestID      | Unique ID of the request                                     |
| RiskRank       | Risk level                                                   |
| ServerName     | Protected domain                                             |
| TimeStamp      | Time of the attack, second-level timestamp                   |
| TopId          | Customer ID                                                  |
| UA             | User-Agent field of the attack request                       |
| Uri            | URI of the attack request                                    |
