# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
### Client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5) c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
       ip=c.recv(1024).decode()
       try:
          c.send(address[ip].encode())
       except KeyError:
          c.send("Not Found".encode())
 ```
### server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
       ip=input("Enter logical Address : ")
       s.send(ip.encode())
       print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
### Server:

<img width="636" height="183" alt="image" src="https://github.com/user-attachments/assets/8bfd1e35-1859-4800-9958-ecce2ed01ebb" />
<br>
### Client:
<br>
<img width="640" height="207" alt="image" src="https://github.com/user-attachments/assets/98986f33-ee5e-4e18-8bdc-e7add7bc0670" />


## PROGRAM - RARP
### server:
```
import socket

s = socket.socket()
s.bind(('localhost', 8001))
s.listen(5)
print("RARP Server is listening...")
c, addr = s.accept()

address = {
    "6A:08:AA:C2": "165.165.80.80",
    "8A:BC:E3:FA": "165.165.79.1"
}

while True:
    mac = c.recv(1024).decode()
    print(f"Received MAC: {mac}")
    ip = address.get(mac, "Not Found")
    c.send(ip.encode())
```
### client:
```
import socket

s = socket.socket()
s.connect(('localhost', 8001))

while True:
    mac = input("Enter MAC Address: ")
    s.send(mac.encode())
    print("IP Address:", s.recv(1024).decode())
```
## OUPUT -RARP
### server:

<img width="633" height="200" alt="image" src="https://github.com/user-attachments/assets/d7fa0b72-efb9-4df1-8fdd-c745bd814167" />
<br>
### client:
<br>
<img width="638" height="232" alt="image" src="https://github.com/user-attachments/assets/791bef39-f7e9-4ae0-b6cf-a59ec5fc8c86" />
<br>
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
