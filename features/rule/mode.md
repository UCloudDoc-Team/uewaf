# Protection Settings

## Working Mode

There are 3 working modes for UWAF rules, namely blocking mode, alert mode, and pass-through mode:

- **Blocking Mode**: Will intercept or allow according to the protection rules
- **Alert Mode**: Will generate attack logs according to the protection rules, but will not intercept attack requests
- **Pass-through Mode**: Will not generate any attack logs, all access requests will be allowed

You can change the working mode at the top of the UWAF rules, information security protection rules tab, or you can click [Edit] after the corresponding domain name in the [Domain Management](/uewaf/features/domain/domain_set) interface, and modify the working mode in the pop-up window.

![](/images/mode-get_mode.png)

!> Note:  
The CC attack protection and blacklist/whitelist functions are controlled by their independent switches under the **Blocking Mode** and **Alert Mode**, and the UWAF rules, CC rules, blacklist/whitelist, etc. are all invalid in the pass-through mode.

## Rule Priority

The priority between the blacklist/whitelist, CC rules, and UWAF rules is (from left to right, the priority decreases in order):

**Global Whitelist > Domain Whitelist > Global Blacklist > Domain Blacklist > Regional IP Ban (Interception) > CC Rules > Custom UWAF Rules > Default UWAF Rules > Information Security Protection Rules**

UWAF rules have independent priorities and can be freely adjusted, but the priority of the default UWAF rules is always lower than that of the custom rules and cannot be adjusted.
