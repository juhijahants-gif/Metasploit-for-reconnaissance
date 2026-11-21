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

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:
<img width="787" height="487" alt="image" src="https://github.com/user-attachments/assets/f2ea0278-0be0-4196-8b60-165b34c3d18c" />


Invoke msfconsole:
## OUTPUT:
<img width="757" height="706" alt="image" src="https://github.com/user-attachments/assets/51619d84-743a-4960-b016-452c479b43da" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.




Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="742" height="303" alt="image" src="https://github.com/user-attachments/assets/dc901809-bc2f-4822-a145-9da8a00f6f99" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
<img width="788" height="277" alt="image" src="https://github.com/user-attachments/assets/b9e36c78-b00d-4727-9ff5-d77c8931ef0d" />



Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
<img width="791" height="596" alt="image" src="https://github.com/user-attachments/assets/4ba4233f-b4ba-494f-8d9e-c84f27d39092" />



Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:
<img width="932" height="600" alt="image" src="https://github.com/user-attachments/assets/2a2b4b49-32b8-4bae-b4cb-5d9ef3b5dfc1" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:

<img width="835" height="745" alt="image" src="https://github.com/user-attachments/assets/ad02c5be-0c50-4776-8cfc-684e660f5081" />


## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="830" height="553" alt="image" src="https://github.com/user-attachments/assets/fad10b5d-7d04-4225-a17e-80c348e32b96" />
<img width="920" height="253" alt="image" src="https://github.com/user-attachments/assets/cc9f78ab-b457-4525-be06-ef28eeb56b91" />

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img width="937" height="752" alt="image" src="https://github.com/user-attachments/assets/548ed0a1-f3c0-4912-9e7f-f39d8ff9cbfb" />

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:
<img width="930" height="362" alt="image" src="https://github.com/user-attachments/assets/d0b7f8c2-3029-4a63-9d21-c83412cbd9c1" />




Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:
<img width="931" height="210" alt="image" src="https://github.com/user-attachments/assets/ac8c2e9d-6606-4102-8851-850edaa9e2f1" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:
<img width="1056" height="742" alt="image" src="https://github.com/user-attachments/assets/8f4df3ec-6309-4a08-ba20-7b8449897ad8" />


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:
<img width="997" height="715" alt="image" src="https://github.com/user-attachments/assets/6524498b-5bbd-4049-8a0c-3654197948ff" />






## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
