# JANANI SHREE A
# 212224100023
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
## client
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
## server
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

![Screenshot 2025-05-02 134049](https://github.com/user-attachments/assets/21e8841d-adc5-4245-a7da-a584ec382a0a)

![Screenshot 2025-05-02 134121](https://github.com/user-attachments/assets/eda5432a-84eb-4e1a-b344-cecf8d927538)


## PROGRAM - RARP
## client 
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
## server
```
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ") 
    s.send(ip.encode())     
    print("Logical Address",s.recv(1024).decode()) 
```
## OUPUT -RARP

![Screenshot 2025-05-02 140706 - Copy](https://github.com/user-attachments/assets/b24eb7d7-d98c-4d3d-a457-1d3ee0e40076)

![Screenshot 2025-05-02 140738](https://github.com/user-attachments/assets/54032b1b-1b3f-4ea7-a509-370c930dd864)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
