# 4. Execution of Network Commands

## AIM  
Use of network commands in a real-time environment.

## Software  
- Command Prompt  
- Network Protocol Analyzer

## Procedure  
To do this experiment, follow these steps:

Students have to understand basic networking commands such as:

- `tcpdump`
- `netstat`
- `ifconfig`
- `nslookup`
- `traceroute`

Additionally, capture **ping** and **traceroute** PDUs using a **network protocol analyzer**.

This includes all commands related to **network configuration**, such as:

- Switching to **privileged mode** and **normal mode**
- Configuring **router interfaces**
- Saving the configuration to **flash memory** or **permanent memory**

### This includes the following commands:

- Configuring the router commands  
- General commands to configure network  
- Privileged mode commands of a router  
- Router processes & statistics  
- IP commands  
- Other IP commands (e.g., `show ip route`)

## Program

### `client.py`

```python
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    h = input("Enter the website you want to ping (or type 'exit' to quit): ")
    s.send(h.encode())
    if h == 'exit': break
    print(s.recv(4096).decode())

s.close()
```
### `server.py`
``` python
import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)
c, _ = s.accept()

while True:
    h = c.recv(1024).decode()
    if h == 'exit': 
        print("Client disconnected.")
        break
    try: c.send(str(ping(h, count=4)).encode())
    except: c.send(b"Ping error")

c.close()
```

## Output

<img width="1245" height="292" alt="image" src="https://github.com/user-attachments/assets/c6b9352d-f6ad-437c-9161-02fcc8ec757c" />

## Result
Thus Execution of Network commands Performed 
