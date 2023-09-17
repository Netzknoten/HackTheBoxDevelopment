![banner](https://github.com/Netzknoten/HackTheBoxDevelopment/assets/114874531/6b81aad7-a78b-4ad9-bc53-2676ca48431f)




​		Repository & Machine Author(s): Manuel Krey

​		

 



### Description:

KreyITSecIn is an easy-level machine on Hack The Box. The objective is to obtain the `user.txt` and `root.txt` flags. The initial access to the machine was achieved by performing a specific set of steps.


## Foothold

To gain an initial foothold on the KreyITSecIn machine, we used the discovered username "bob" and initiated an SSH brute-force attack using Metasploit. We used the rockyou.txt password list located in `/usr/share/wordlists/` for the attack.


## Conclusion

KreyITSecIn was an easy-level machine on Hack The Box that involved using Metasploit for an SSH brute-force attack with the rockyou.txt password list to access the machine. Once inside, we obtained both the user and root flags, which were represented as MD5 hashes of the respective passwords.

---

Please replace `<machine_ip>`, `<user_flag_md5_hash>`, and `<root_flag_md5_hash>` with the actual IP address of the KreyITSecIn machine and the corresponding MD5 hash values for the flags. Adjust the rest of the write-up according to your actual steps and commands.

[Machine_Name.md](https://github.com/Netzknoten/HackTheBoxDevelopment/files/12641548/Machine_Name.md)

Skeleton writeups for community challenge and machine submissions 💚
