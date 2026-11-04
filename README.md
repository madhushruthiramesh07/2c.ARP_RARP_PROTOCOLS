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
```
SERVER

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

```
CLIENT

import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True: 
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP
<img width="627" height="84" alt="image" src="https://github.com/user-attachments/assets/dcac1ce1-4913-40cc-b948-16e0216aa67d" />
<img width="642" height="169" alt="image" src="https://github.com/user-attachments/assets/2a58c8bb-2f1b-40ad-9005-c6c384a4a6de" />

## PROGRAM - RARP
```
SERVER

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

```
CLIENT

import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP
<img width="640" height="99" alt="image" src="https://github.com/user-attachments/assets/e56af1e1-a7a3-4fa3-887b-1f17c0eb864c" />
<img width="812" height="157" alt="image" src="https://github.com/user-attachments/assets/d0052539-9a0d-4524-bad4-bdb0dda11cfc" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
