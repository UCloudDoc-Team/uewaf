# Overview

The overview provides dynamic information related to the user's UWAF product, including information announcements, basic product information, attack situation perception maps, and attacks within 24 hours. You can view the quota information of the version, and if a certain quota is not enough, you can purchase the corresponding expansion pack through [Quota Management](/uewaf/features/info/quota_management).

- A - [Product Operation](/uewaf/features/info/info?id=Product Operation)
- B - [Basic Information](/uewaf/features/info/info?id=Basic Information)
- C - [Quota Information](/uewaf/features/info/info?id=Quota Information)
- D - [Security Situation Awareness](/uewaf/features/info/info?id=Security Situation Awareness)
- E - [Attack Request Information](/uewaf/features/info/info?id=Attack Request Information)
- F - [Requests and Attacks](/uewaf/features/info/info?id=Requests and Attacks)

![](/images/info-get_info.png)

## Product Operation

Product operation includes four buttons, each with the following functions:

- Close UWAF: Delete UWAF resources, you need to delete all domains in [Domain Management](/uewaf/features/domain/domain_set) first
- Change Version: Upgrade the existing UWAF product version, downgrade is not supported after upgrade
- Renewal: Jump to the product renewal interface, where you can turn on or off automatic renewal or change the billing method
- Documentation Center: Jump to the official [UWAF Product Documentation](/uewaf/README)

## Basic Information

Basic information includes the basic information of the product:

- Resource ID: The unique identifier of the product resource
- UWAF Version: Enterprise Edition, Flagship Edition, or Customized Edition
- Expiration Time: The expiration time of the product resource. If it is not renewed after expiration, resources will be recycled according to the [Recycling Strategy](/uewaf/steer/recycling_strategy)
- Billing Method: Monthly or yearly
- <div id="back-ips"></div>Back to IP: Click the [View] button to view the back-to-source network segment of the product resource that has been opened

## Quota Information

This is only part of the quota information (for detailed quota information, see [Performance and Quota Comparison](/uewaf/steer/version_selection?id=Performance and Quota Comparison)). The progress bar above is the quota usage rate, and the starting value on the left below is fixed at 0, and the right is the actual quota of the product resource (including the purchased expansion pack). Click [Quota Management](/uewaf/features/info/quota_management) to purchase expansion packs.

Quota information includes the following quota information and its usage:

- Domain usage: The number of domains added, regardless of the wildcard domain, the wildcard domain quota is: domain number configuration / 10
- [Exclusive IP](/uewaf/features/domain/domain_set?id=exclusive-ip) usage: The number of exclusive IP points used
- Bandwidth usage: The bandwidth usage of the product resource, the statistical granularity is the average value of five minutes, if the actual bandwidth used is too low, it will be displayed as 0.00%

## Security Situation Awareness

Security situation awareness can view the attack source of all domains or specific domains. The deployment area will be marked with a purple positioning symbol, and the area with attack traffic will be marked on the global map, with a dynamic arrow effect from the attack source area to the deployment area indicating attacks initiated from a certain source area within 24 hours. Due to front-end performance considerations, the default display is the security situation awareness map of the last 24 hours or the first 1000 attack logs.

## Attack Request Information

Attack request information shows some detailed information of the attack logs in the security situation awareness, including attack time, target domain of the attack, source IP, region of the source IP, and attack type, sorted in reverse chronological order.

## Requests and Attacks

Requests and Attacks show the total number of requests and total number of attacks in the last 24 hours, allowing you to have a general understanding of the access and attack situation of the domain.
