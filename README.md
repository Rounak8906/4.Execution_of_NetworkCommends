# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>
## Program
Server.py

```
import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server listening on port 8000...")
c, addr = s.accept()
print(f"Connection from {addr}")

while True:
    try:
        hostname = c.recv(1024).decode('utf-8')
        if not hostname or hostname.lower() == 'exit':
            print("Client disconnected.")
            break
        response = ping(hostname, verbose=False, count=4)
        c.send(str(response).encode('utf-8'))
    except Exception as e:
        c.send(f"Ping failed: {e}".encode('utf-8'))

c.close()
```
Client.py
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter the website you want to ping (or type 'exit' to quit): ")
    s.send(ip.encode('utf-8'))
    if ip.lower() == 'exit':
        break
    print(s.recv(4096).decode('utf-8'))

s.close()
```
## Output
Client
<img width="783" height="248" alt="image" src="https://github.com/user-attachments/assets/ad706305-c864-4439-9c67-f55f81ee4e67" />
Server
<img width="781" height="189" alt="image" src="https://github.com/user-attachments/assets/2e84f279-0e51-423f-a645-b9783501bb66" />
netstat
<img width="615" height="700" alt="image" src="https://github.com/user-attachments/assets/eb3eb1c1-e548-4284-9493-aefbb1de1ffb" />

ipconfig
<img width="959" height="720" alt="image" src="https://github.com/user-attachments/assets/d1727b9f-26d1-477d-ae8d-fddad7a4e9cd" />

nslookup
<img width="959" height="723" alt="image" src="https://github.com/user-attachments/assets/25d4dc6f-2f69-448b-b853-2b150439cb33" />

traceroute
<img width="1165" height="497" alt="image" src="https://github.com/user-attachments/assets/63fceb10-7fc6-4b9e-96d1-2cfaf39fef62" />

tcpdump
<img width="1157" height="711" alt="image" src="https://github.com/user-attachments/assets/92a65efd-6294-4221-bae4-ce9c10a5c7e3" />

## Result
Thus Execution of Network commands Performed 
