## Rule Synchronization

UWAF supports rule synchronization for all types of custom rules. The "Rule Synchronization" button is located to the right of the "Add Rule" button.

There are two methods for rule synchronization:

- Append mode: The rules under the current domain name are copied and appended to other target domain names without affecting the original rules of the target domain names;
- Overwrite mode: The rules under the target domain names are first deleted, and then the rules under the current domain name are copied and overwritten to the target domain names. The original rules of the target domain names will be cleared.

When synchronizing rules to other domain names, the append mode will incrementally add rules to the corresponding domain names, while the overwrite mode will **replace the old rules with new rules**, please use it with caution! In cases where there are many rules or many selected domain names, please synchronize in batches, otherwise, a timeout may occur.

![](/images/rule_sync-sync_rule.png)
