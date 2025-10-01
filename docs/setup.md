```
Windows Forwarder Input File
[default]
host = DESKTOP-3LHSK7J

[WinEventLog://Application]
disabled = 0
index = windows

[WinEventLog://Security]
disabled = 0
index = windows

[WinEventLog://System]
disabled = 0
index = windows

[WinEventLog://Microsoft-Windows-Sysmon/Operational]
disabled = 0
index = windows
renderXml = true
sourcetype = XmlWinEventLog:Microsoft-Windows-Sysmon/Operational


Windows Forwarder Output File

Ubuntu Server Forwarder Input File
Ubuntu Server Forwarder Output File
```
