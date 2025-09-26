### Brute Force Simulation
I used Hydra to simulate a brute force attack against the Linux forwarder. Originally, I was planning on just manually entering the passwords wrong to simulate this attack but it felt boring and uninspiring.

command: -l justy -P /home/juce/Documents/passwords.txt ssh://10.0.0.40

where -l to specify the username since we know it. -P to tell Hydra to use a list of passwords. Just a text file with 200 common passwords from 2020.

![hydra](https://github.com/user-attachments/assets/249295f0-b3d5-4c22-b926-b64d7f95097e)
