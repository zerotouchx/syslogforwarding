# SyslogForwarding configuration with Ansible on Lenovo FLEX Blade Servers


**Ansible Ad-hoc Command**

With the ansible ad-hoc command below you can set the syslog forwarding without login to the IMM .

```shell
ansible <Blade Servers/Blade Server Groups> -i <inventory> -m raw -a "alertentries -1 -type syslog -status on -n syslogForwarding -ip <central syslog server> -pn 514 -crt all -crten enabled -wrn all -wrnen enabled -sys all -sysen enabled" -u USERID --ask-pass
```

**Do not forget to modify the fields with brackets (<>) in accordance with your environment.**


[**Reference:** <em>All the information below taken from the URL</em>] ftp://ftp.software.ibm.com/systems/support/system_x_pdf/88y7599.pdf


Use the alertentries command to manage alert recipients.
-  alertentries with no options displays all alert entry settings.
-  alertentries -number -test generates a test alert to the given recipient index
number.
-  alertentries -number (where number is 0-12) displays alert entry settings for the
specified recipient index number or allows you to modify the alert settings for
that recipient.

The following table shows the arguments for the options.



| Option              | Description                                                     | Values                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|---------------------|-----------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| -number             | Alert recipient index number to display, add, modify, or delete | 1 through 12                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| -status             | Alert recipient status                                          | On, off                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -type               | Alert type                                                      | Email, syslog                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| -log                | Include event log in alert email                                | On, off                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -n                  | Alert recipient name                                            | String                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| -e                  | Alert recipient email address                                   | Valid email address                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| -ip                 | Syslog IP address or hostname                                   | Valid IP address or hostname                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| -pn                 | Syslog port number                                              | Valid port number                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| -del                | Delete specified recipient index number                         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| -test               | Generate a test alert to specified recipient index number       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| -crt                | Sets critical events that          send alerts                  | All,none, custom:te\|vo\|po\|di\|fa\|cp\|me\|in\|re\|ot Custom critical alert settings are specified using a pipe separated list of values of the form alertentries -crt  custom:te\|vo, where custom values are\:                                       
                                                  - te: critical temperature threshold exceeded  
                                                  - vo: critical voltage threshold exceeded     
                                                  - po: critical power failure  
                                                  - di: hard disk drive failure  
                                                  - fa: fan failure  
                                                  - cp: microprocessor failure 
                                                  - me: memory failure  
                                                  - in: hardware incompatibility  
                                                  - re: power redundancy failure  
                                                  - ot: all other critical events            





| Option 	| Description                          	| Values                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         	|
|--------	|--------------------------------------	|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| -crten 	| Send critical event alerts           	| Enabled, disabled                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              	|
| -wrn   	| Sets warning events that send alerts 	| All, none, custom:rp|te|vo|po|fa|cp|me|ot Custom warning alert settings are specified using a pipe separated list of values of the form alertentries   - wrn custom:rp|te, where custom values are:- rp: power redundancy warning - te: warning temperature threshold exceeded - vo: warning voltage threshold exceeded - po: warning power threshold exceeded - fa: non-critical fan event - cp: microprocessor in degraded state - me: memory warning  - ot: all other warning events                        	|
| -wrnen 	| Send warning event alerts            	| Enabled, disabled                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              	|
| -sys   	| Sets routine events that send alerts 	| All, none, custom:lo|tio|ot|po|bf|til|pf|el|ne Custom routine alert settings are specified using a pipe separated list of values of the form alertentries -sys custom:lo|tio, where custom values are: - lo: successful remote login - tio: operating system timeout - ot: all other informational and system events - po: system power on/off - bf: operating system boot failure - til: operating system loader watchdog timeout - pf: predicted failure (PFA) - el: event log 75% full - ne: network change 	|
| -sysen 	| Send routine event alerts            	| Enabled, disabled                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              	|



```bash
Syntax:
alertentries [options]
options:
-number recipient_number
-status status
-type alert_type
-log include_log_state
-n recipient_name
-e email_address
-ip ip_addr_or_hostname
-pn port_number
-del
-test
-crt event_type
-crten state
-wrn event_type
-wrnen state
-sys event_type
-sysen state
```




## Disclaimer

  <em>**"[The author] assumes no responsibility or liability for any errors or omissions in the content of this site. The information contained in this site is provided on an “as is” basis with no guarantees of completeness, accuracy, usefulness or timeliness…"**</em>