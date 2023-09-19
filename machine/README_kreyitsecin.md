# Hack The Box - KreyITSecIn Write-up

![Banner](assets/images/banner.png)

<img src="assets/images/htb.png" style="margin-left: 20px; zoom: 60%;" align="left" />
<font size="10">KreyITSecIn</font>

16<sup>th</sup> September 2023

Machine Author(s): Manuel Krey

### Description

This machine...

### Objective

Our objective was to perform reconnaissance and gain access to the machine.

### Difficulty

`easy`

### Flags

User: `HTB{user_flag_md5_hash}`  
Root: `HTB{root_flag_md5_hash}`

# Enumeration

Initial enumeration was performed to gather information about the KreyITSecIn machine. This included identifying open ports, services, and potential vulnerabilities.

### Port Scanning

We conducted a port scan using the following command:

```shell
nmap -p- -A -T4 -sV <machine_ip>
