![](assets/images/banner.png)



<img src="/home/debuser/HackTheBox-Development/HackTheBoxDevelopment/machine/assets/images/KreyITSecIN.jpeg" style="margin-left: 20px; zoom: 60%;" align=left />    	<font size="10">KreyITSecIn</font>

​		16<sup>th</sup> September 2023

​		Machine Author(s): Manuel Krey

​		

 



### Description:

KreyITSecIn is an easy-level machine on Hack The Box. The objective is to obtain the `user.txt` and `root.txt` flags. The initial access to the machine was achieved by performing a specific set of steps.


### Difficulty:

`easy`

### Flags:

User: `<md5>`

Root: `<md5>`

## Introduction

KreyITSecIn is an easy-level machine on Hack The Box. The objective is to obtain the `user.txt` and `root.txt` flags. The initial access to the machine was achieved by guessing the SSH login credentials for the user "bob" and the root user.

## Enumeration

Initial enumeration was performed to gather information about the KreyITSecIn machine. This included identifying open ports, services, and potential vulnerabilities.

### Port Scanning

We conducted a port scan using the following command:

```shell
nmap -p- -A -T4 -sV <machine_ip>
```

From the scan, we identified the following:

- Port 22 (SSH) is open.

### OSINT for Username

During the enumeration process, we also conducted open-source intelligence (OSINT) research to gather additional information. We discovered that the username "bob" or the name "Bob Hackwell" was publicly available on a website entry.

This information was used to assist in the enumeration process and played a crucial role in identifying the username used to gain access to the machine.

## Foothold

To gain an initial foothold on the KreyITSecIn machine, we used the discovered username "bob" and initiated an SSH brute-force attack using Metasploit. We used the rockyou.txt password list located in `/usr/share/wordlists/` for the attack.

```shell
use auxiliary/scanner/ssh/ssh_login
set RHOSTS <machine_ip>
set USER_FILE myuserlist.txt
set PASS_FILE /usr/share/wordlists/rockyou.txt
set VERBOSE true
exploit
```

After several attempts, we successfully guessed the password for the user "bob" as "123456."

```shell
ssh bob@<machine_ip>
Password: 123456
```

## User Privilege Escalation

Once logged in as "bob," we navigated to the `/home/bob/` directory and found the "user.txt" flag. The flag was a hash value representing the user flag.

```shell
cat user.txt
```

### User Flag (MD5 Hash)

The user flag is an MD5 hash of the root password. The MD5 hash for the user flag is: `<user_flag_md5_hash>`

## Root Privilege Escalation

To escalate privileges to root, we used the MD5 hash of the root password, which is "25f9e794323b453885f5181f1b624d0b," and attempted to switch to the root user.

```shell
su -
Password: 25f9e794323b453885f5181f1b624d0b
```

Once we provided the correct root password hash, we successfully logged in as the root user.

### Root Flag (MD5 Hash)

The root flag is an MD5 hash of the root password. The MD5 hash for the root flag is: `<root_flag_md5_hash>`

## Conclusion

KreyITSecIn was an easy-level machine on Hack The Box that involved using Metasploit for an SSH brute-force attack with the rockyou.txt password list to access the machine. Once inside, we obtained both the user and root flags, which were represented as MD5 hashes of the respective passwords.

---

Please replace `<machine_ip>`, `<user_flag_md5_hash>`, and `<root_flag_md5_hash>` with the actual IP address of the KreyITSecIn machine and the corresponding MD5 hash values for the flags. Adjust the rest of the write-up according to your actual steps and commands.
