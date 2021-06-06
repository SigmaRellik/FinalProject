# Red Team: Summary of Operations

## Table of Contents
- Exposed Services
- Critical Vulnerabilities
- Exploitation

### Exposed Services
_TODO: Fill out the information below._

Nmap scan results for each machine reveal the below services and OS details:

```bash
$ nmap 192.168.1.0/24
```
![](Resources/1.1.png)


This scan identifies the services below as potential points of entry:
- Target 1
  - ssh
  - http
  - rpcbind
  - netbio-ssn

![](Resources/1.2.png)

The following vulnerabilities were identified on each target:
- Target 1
  - OpenSSH
  - Wordpress Enumeration
  - SQL database access
  - root access with python

![](Resources/1.3.png)
![](Resources/1.4.png)
![](Resources/1.5.png)


### Exploitation
_TODO: Fill out the details below. Include screenshots where possible._

The Red Team was able to penetrate `Target 1` and retrieve the following confidential data:
- Target 1
  - `flag1.txt`: b9bbcb33e11b80be759c4e844862482d
    - **Exploit Used**
      - After gaining access to Michael's grep "flag" inside /var/www/html
  ![](![](Resources/1.6.png)
  - `flag2.txt`: fc3fd58dcdad9ab23faca6e9a36e581c
    - **Exploit Used**
      - Guessing Michael's password to log in via SSH, and search for flag inside /var/www/html
   ![](Resources/1.7.png)
   ![](Resources/1.12.png)
  - `flag3.txt`: afc01ab56b50591e7dccf93122770cd2
      - **Exploit Used**
      - Using credientials found inside `wp-config.php` to log into MySQL
    ![](Resources/1.8.png)
    ![](Resources/1.9.png)
    ![](Resources/1.10.png)
  - `flag4.txt`: 715dea6c055b9fe3337544932f2941ce
      - **Exploit Used**
      - after using john to get the credentials of Steven from the hash found inside MYSQL. We used a python script to escalate privileges
   ![](Resources/1.11.png)
   ![](Resources/1.13.png)
   ![](Resources/1.14.png)
