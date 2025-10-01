### Brute Force Simulation
I used Hydra to simulate a brute force attack against the Linux forwarder. Originally, I was planning on just manually entering the passwords wrong to simulate this attack but it felt boring and uninspiring.

command: ```-l justy -P /home/juce/Documents/passwords.txt ssh://10.0.0.40```

where -l to specify the username since we know it. -P to tell Hydra to use a list of passwords. Just a text file with 200 common passwords from 2020.

![hydra](https://github.com/user-attachments/assets/249295f0-b3d5-4c22-b926-b64d7f95097e)


### T1197 Bits Job Simulation
To simulate this attack, i used Atomic Red Team. Atomic Red Team is an open-source library and PowerShell-based framework that provides simple, focused tests to emulate adversary tactics, techniques, and procedures (TTPs) mapped to the MITRE ATT&CK framework

T1197: BITS Jobs as a specific technique used by adversaries to execute code persistently and perform various background tasks on targeted Windows systems. BITS is an acronym for Windows Background Intelligent Transfer Service, which is a low-bandwidth, asynchronous file transfer mechanism exposed through Component Object Model (COM). BITS is designed for background operations, such as system updaters, using available idle bandwidth without interfering with other networked applications.

Open up Powershell as admin, use the command ```Invoke-AtomicTest T1197```

![bits result](https://github.com/user-attachments/assets/2beaaebe-15fd-4414-8fb4-2ca3d8c61d5c)

Refer to the detections.md document to see the results in Splunk!
