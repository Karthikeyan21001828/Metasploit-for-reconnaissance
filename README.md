# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## step4:

use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

## EXECUTION STEPS AND ITS OUTPUT:
## PROGRAM:

Find out the ip address of the attackers system



## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Metasploit-for-reconnaissance/assets/93427303/6d7e4062-83ae-45ec-8e66-35e691f9e817)

## Invoke msfconsole:


## OUTPUT:

![image](https://github.com/Karthikeyan21001828/Metasploit-for-reconnaissance/assets/93427303/836195f8-8d34-476b-b3f9-d0f414de70fe)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.







## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Metasploit-for-reconnaissance/assets/93427303/c43897e3-86ad-488a-bee3-6e5c6ea40f2a)

## Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Metasploit-for-reconnaissance/assets/93427303/12df1832-a046-4df8-b57d-a094c274b57b)

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Metasploit-for-reconnaissance/assets/93427303/fd71cb7f-2e71-4ffa-94a5-2db00f476663)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Metasploit-for-reconnaissance/assets/93427303/14573fd9-a434-4387-a47c-7cf21ea5ccea)

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Metasploit-for-reconnaissance/assets/93427303/caf4ccf4-6b39-46c7-85c2-e12704a6940a)

The info command provides information regarding a module or platform,

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Metasploit-for-reconnaissance/assets/93427303/b572f203-6cc6-4032-bd64-dbe0e0010c54)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Metasploit-for-reconnaissance/assets/93427303/571fe9b2-807b-48d2-8a32-83feae1ff185)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Metasploit-for-reconnaissance/assets/93427303/43e7fe8a-8013-4e67-98b7-95ffd21df7ef)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Metasploit-for-reconnaissance/assets/93427303/a0600a43-30a4-4fde-b342-f74be218e50c)

Use the set rhosts command to set the parameter and run the module, as follows:

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Metasploit-for-reconnaissance/assets/93427303/fa54c1da-e313-4fe9-816b-f1806906753d)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Metasploit-for-reconnaissance/assets/93427303/c85bb55d-6c5e-4ed7-b86e-e0a25b192a0d)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true

## OUTPUT:
![image](https://github.com/Karthikeyan21001828/Metasploit-for-reconnaissance/assets/93427303/abc16def-5e10-433d-a022-5a712a239e90)

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
