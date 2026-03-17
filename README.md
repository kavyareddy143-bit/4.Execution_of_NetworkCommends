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

## Output
<img width="983" height="306" alt="image" src="https://github.com/user-attachments/assets/00b60027-97ad-476f-90ce-ff53d912125f" />
```
server.py
```
```
import socket

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

server_socket.bind(('localhost', 12345))

server_socket.listen(1)
print("Server is waiting for connection...")

conn, addr = server_socket.accept()
print("Connected by", addr)

while True:
    data = conn.recv(1024).decode()
    if not data:
        break
    print("Client:", data)

    conn.send(("Reply: " + data).encode())

conn.close()
server_socket.close()
```
```
client.py
```
```
import socket

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

client_socket.connect(('localhost', 12345))

while True:
    message = input("Enter message: ")
    client_socket.send(message.encode())

    data = client_socket.recv(1024).decode()
    print("Server:", data)

client_socket.close()
```
<img width="700" height="270" alt="image" src="https://github.com/user-attachments/assets/777381e3-9c00-44fe-83a9-24706091868c" />
```
server.py
```
```
import socket

server_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
server_socket.bind(('localhost', 9999))

print("Server is ready...")

while True:
    message, addr = server_socket.recvfrom(1024)
    print("Received from client:", message.decode())

    reply = "Hop reached / Reply from server"
    server_socket.sendto(reply.encode(), addr)
```
```
client.py
```
```
import socket
import time

server_address = ('localhost', 9999)

client_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
client_socket.settimeout(2)

ttl = 1
max_hops = 5

print("Traceroute simulation:\n")

while ttl <= max_hops:
    client_socket.setsockopt(socket.IPPROTO_IP, socket.IP_TTL, ttl)

    try:
        start = time.time()
        client_socket.sendto(f"Packet with TTL={ttl}".encode(), server_address)

        data, _ = client_socket.recvfrom(1024)
        end = time.time()

        print(f"Hop {ttl}: Reply received in {round((end-start)*1000)} ms")

    except socket.timeout:
        print(f"Hop {ttl}: Request timed out")

    ttl += 1

client_socket.close()
```

<img width="706" height="228" alt="image" src="https://github.com/user-attachments/assets/d390e0ea-981d-4d2c-986a-015e7c2da2e6" />
<img width="865" height="348" alt="image" src="https://github.com/user-attachments/assets/6173151f-6a2b-4f7c-ba77-feacc1af81a6" />
<img width="625" height="312" alt="image" src="https://github.com/user-attachments/assets/375e3b01-5828-446d-aa1f-7fb236cd66b5" />
<img width="674" height="305" alt="image" src="https://github.com/user-attachments/assets/20c5a0c7-a67d-4988-a454-b1bc393c8f44" />
<img width="907" height="934" alt="image" src="https://github.com/user-attachments/assets/16eba211-3734-4dcf-88cf-cbb364357710" />
<img width="535" height="91" alt="image" src="https://github.com/user-attachments/assets/819f2ecb-0e5a-48a4-b543-049a6a774e7f" />
<img width="1060" height="791" alt="image" src="https://github.com/user-attachments/assets/d31ae44c-ce6b-476b-83b3-3a539400c1d7" />
<img width="942" height="814" alt="image" src="https://github.com/user-attachments/assets/08826bbd-b30c-42c2-96ae-a18028844f49" />
<img width="990" height="179" alt="image" src="https://github.com/user-attachments/assets/6055cd42-db94-4b1b-9ad4-1a59796ca9b8" />
<img width="989" height="792" alt="image" src="https://github.com/user-attachments/assets/9086d4d3-ef18-4128-a673-5827cc0b2edb" />
<img width="1218" height="912" alt="image" src="https://github.com/user-attachments/assets/975058a5-08fe-4b0b-a1ca-77490d2b8da5" />



## Result
Thus Execution of Network commands Performed 
