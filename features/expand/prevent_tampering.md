# Web Page Tampering Prevention

The web page tampering prevention feature can ensure that the web pages returned by UWAF are not tampered with, even if some web page files on the source station are maliciously tampered with. The principle is that after adding a rule, the first time the URL in the rule is accessed, UWAF will cache the static web page file corresponding to that URL. The second time this URL is accessed, the source station will not be requested. When the web page is updated, the cache needs to be manually updated.

![](/images/prevent_tampering-get_rule.png)

!> Note:  
The URL domain name added must be consistent with the domain name selected in the top domain name selection box.

## Add Rule

You can add tampering prevention rules for URLs.

### Parameter Description

| Parameter     | Description                                                  |
| ------------- | ------------------------------------------------------------ |
| Business Name | Rule name                                                    |
| URL           | The address of the static web page file that needs to be protected. You need to fill in the complete link of the **static file** of html or htm |
| Status        | Control the status of a single tampering prevention rule, you can 【Enable Protection】or【Disable Protection】 |

For example: To enable web page tampering prevention for the static web page file of this URL `https://example.com/some_activities.html`, add a rule as shown in the figure below:

![](/images/prevent_tampering-add_rule.png)

## Global Tampering Prevention Switch

The 【Web Page Tampering Prevention】switch next to 【Add Rule】is the global switch to control web page tampering prevention. When it is off, all tampering prevention rules are ineffective. When it is on, the tampering prevention rules are determined by their own protection status.

## Remarks

1. How to change the【Protection Status】?  
   You can click the 【Edit】button behind the corresponding rule column, and complete it in the rule editing box that pops up.

2. What is the use of【Update Cache】?  
   When you have modified your web page, updating the cache can clear the cache on the UWAF side.
