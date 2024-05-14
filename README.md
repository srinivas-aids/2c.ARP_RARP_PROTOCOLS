# EX.NO:2c                SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
### Client:
1. Start the program</br>
2. Using socket connection is established between client and server.</br>
3. Get the IP address to be converted into MAC address.</br>
4. Send this IP address to server.</br>
5. Server returns the MAC address to client.</br>
### Server:
1. Start the program</br>
2. Accept the socket which is created by the client.</br>
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.</br>
4. Read the IP address which is send by the client.</br>
5. Map the IP address with its MAC address and return the MAC address to client.</br>

## PROGRAM - ARP
### Client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
 ip=c.recv(1024).decode()
 try:
 c.send(address[ip].encode())
 except KeyError:
 c.send("Not Found".encode())
```
### Server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address : ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())
```
## PROGRAM - RARP
### Client:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
 ip=c.recv(1024).decode()
 try:
   c.send(address[ip].encode())
 except KeyError:
   c.send("Not Found".encode())
```
### Server:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT - ARP
![image](https://github.com/Yuvaranithulasingam/2c.ARP_RARP_PROTOCOLS/assets/121418522/f1672c11-b0d6-4d4a-b076-d81b505c4e50)

## OUPUT -RARP
![image](https://github.com/Yuvaranithulasingam/2c.ARP_RARP_PROTOCOLS/assets/121418522/34ab84eb-9e13-4449-b899-9128d5988d16)

## RESULT
Thus, the python program for simulating ARP and RARP protocols using TCP was successfully 
executed.
