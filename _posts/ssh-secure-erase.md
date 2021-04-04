---
title: SSD Secure Erase
date:  2021-03-24 19:00:00
---

Before secure release, it must not be frozen.  Can use the following command to keep track of status of drive.
---
``` bash
hdparam -I /dev/drive
```

Look for `frozen` in output:
```
Security: 
       Master password revision code = 65534
               supported
       not     enabled
       not     locked
               frozen
       not     expired: security count
```

If still `frozen`, attempt hybernation/reset
``` bash
echo -n mem > /sys/power/state
```

Set password
---
Need to set password first
``` bash
hdparm --user-master u --security-set-pass password /dev/drive
```

Securely Erase Data
---
Use password to do secure erase
``` bash
hdparm --user-master u --security-erase password /dev/drive
```


Link to original info: [SSD_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)
