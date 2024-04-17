# Source Site Status Monitoring

UWAF will use the HEAD method to probe and send requests to the domain source sites added by users. If there are 3 consecutive abnormal responses within 5 minutes, an alert email or SMS will be sent to the corresponding message subscription group users. The frequency is once every 5 minutes.

!> Note:  
If there are restrictions on the probing IP of UWAF by the source site (such as a whitelist or blacklist), it may cause false alarms.

## Handling of Source Site Status Alerts

When you receive an email or SMS alert about the source site status, please follow the steps below to check:

1. Confirm that the monitoring address is correctly configured, if not set, you can skip this step

2. Check the domain access situation in the 'System Overview' under 'Security Report' to see if a sudden increase in traffic has caused excessive pressure on the source site

3. Check whether the source site server is working normally, mainly whether the CPU usage rate and bandwidth usage rate are too high

4. Check the whitelist and blacklist of the source site, and whether the back-to-source address of UWAF has been added to the whitelist

5. Check whether the regional IP blocking or other rules have mistakenly blocked the probing IP of UWAF

If you confirm that the source site is normal and has not intercepted the probing requests of UWAF, and your business is affected at this time, you can go to 'Domain Management', select the corresponding domain entry, click on 'More' option, select '[Back-to-source Settings](/uewaf/features/domain/monitor_set.md?id=back-to-source-settings)', and click on '[Business Back-to-source](/uewaf/features/domain/monitor_set.md?id=business-back-to-source)', or consult technical support for help.
