Brute Force Simulation
I used Hydra to simulate a brute force attack against the Linux forwarder. Originally, I was planning on just manually entering the passwords wrong to simulate this attack but it felt boring and uninspiring. So 
hydra -l justy -P /home/juce/Documents/passwords.txt ssh://10.0.0.40
where -l to specify the username since we know it. -P to tell Hydra to use a list of passwords. Just a text file with 200 common passwords from 2020.
