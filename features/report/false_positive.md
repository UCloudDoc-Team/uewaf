# False Positive Details

False positive details allow you to view all attack logs that have been marked as false positives for the current domain. You can also query the details of the attack log or cancel the false positive.

The false positive feature is designed to adapt to a variety of Web business situations, allowing UWAF's default rules to not affect normal business. Logs marked as false positives actually cancel the rules triggered by the attack request corresponding to the log, rather than whitelisting the URL or other HTTP protocol content. After being marked as a false positive, the rule will not be judged subsequently.

![](/images/false_positive-get_attack.png)

## Marking False Positives for Business

After the business is connected to UWAF, it is recommended to first enable the alert mode and observe whether there are any attack logs generated. After a period of time, if there are no attack logs or only a small number of attack logs that are real attacks rather than normal business after the business traffic passes through UWAF, you can enable blocking mode.

If there are a large number of attack logs and most of them are triggered by normal business, you can first mark the same URL in the attack logs as false positives. The same URL can be marked once, wait for five minutes, then select the most recent five minutes as the time period and observe the newly generated attack logs. Repeat the above process until there are no attack logs generated or all attack logs are real attacks.
