
# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting
#### NAME: PRIYADHARSHINI R K
#### REGISTER NUMBER:212223040155
# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## Architecture Diagram
```
+----------------------+              +--------------------+             +-------------------------+
|    Attacker Machine  |<----------->|  Target (MySQL DB) |<----------->|       Network           |
|  (Kali Linux + MSF)  |              |    Port 3306       |             | (LAN or External)      |
+----------------------+              +--------------------+             +-------------------------+
         |
         | Metasploit Initialized (msfdb init)
         |
         |-- db_nmap: Port Scan and Service Discovery
         |
         |-- auxiliary/scanner/mysql/mysql_version
         |      --> Detects MySQL Version
         |
         |-- auxiliary/scanner/mysql/mysql_login
                --> Brute-force user login
```

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
### OUTPUT:
Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
```
sudo systemctl start postgresql
msfdb init
msfconsole
```
### OUTPUT:
<img width="834" height="456" alt="image" src="https://github.com/user-attachments/assets/f0670d7c-48ee-4a1e-8eb4-595072d26fd5" />
<img width="674" height="363" alt="image" src="https://github.com/user-attachments/assets/3917dcef-9aa4-45f4-a779-252f17f1791c" />
<img width="840" height="784" alt="image" src="https://github.com/user-attachments/assets/5624c3d6-b642-4b8e-acaf-b4af9df9df25" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
```
nmap -sT 192.168.1810/24 -p1-1000
```
### OUTPUT:
<img width="872" height="507" alt="image" src="https://github.com/user-attachments/assets/e9a9cb8b-96b9-45b7-8310-55beee68a104" />


**step4:**
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
```
db_nmap -sV -sC -p 3306 <target-ip>
