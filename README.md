# 2c.SIMULATING ARP /RARP PROTOCOLS
### NAME: D.B.V.SAI GANESH
### REG NO: 212223240025
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
## OUPUT - ARP:
### Client:
![image](https://github.com/user-attachments/assets/d941c6e3-2864-42c6-90b8-3e0875eb7248)

### Server:
![image](https://github.com/user-attachments/assets/01404378-b8dd-4017-9bcc-24c209d832df)

## PROGRAM - RARP:
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
## OUPUT -RARP:
### Client:
![image](https://github.com/user-attachments/assets/c1485cb7-b2fe-4f19-8f3b-544e3b10ed11)

### Server:
![image](https://github.com/user-attachments/assets/aa3a1dff-63be-43c4-8a60-9039ea8e5454)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
