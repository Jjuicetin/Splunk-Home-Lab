### Brute Force Detection
![detections](https://github.com/user-attachments/assets/47d88c3c-eec2-4532-94ae-ca2d29331ae7)

![bits detection table](https://github.com/user-attachments/assets/b4c6bd83-d747-49eb-bff5-c5d5ed38cd8f)

### Bits Persistance Detection
Command: index=windows (source="xmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode="1") OR (source="WinEventLog:Security" EventCode="4688")
(Image="*bitsadmin.exe" OR OriginalFileName="bitsadmin.exe")
(CommandLine="*transfer*" OR CommandLine="*addfile*")
| table _time, Image, CommandLine, ParentImage, ParentCommandLine, User

Basically saying to filter the logs in Sysmon where EventCode is 1 or look in Windows Security Log where EventCode is 4688 and look for traces of bitsadmin or look for commandline queries with "transfer or addfile"

**What is Event Code 4688 in Windows Security Logs?**

Event Code 4688 is a built-in Windows security log event for process creation.

**What is Event Code 1 in Sysmon?**

Compared to the standard Windows Event Code 4688, it gives you way more detail about process creation, like command-line arguments and file hashes. That extra info makes it great for spotting threats. Still, 4688 is worth paying attention to because it’s turned on by default and can fill the gap if Sysmon isn’t running on the system.


![bits splunk](https://github.com/user-attachments/assets/52c5578f-6ca7-4377-8b2d-efb1beec1600)
