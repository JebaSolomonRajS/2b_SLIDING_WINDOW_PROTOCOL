# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
To write a python program to perform sliding window protocol 
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
Client.py
```
import socket
from datetime import datetime
 
s=socket.socket()
 
s.bind(('localhost',8080))
 
s.listen(5)
c,addr=s.accept()
print("Client Address : ",addr)
 
now = datetime.now()
 
c.send(now.strftime("%d/%m/%Y %H:%M:%S").encode())
ack=c.recv(1024).decode()
 
if ack:
    print(ack)
c.close()


```

Server.py
```
import socket 
s=socket.socket() 
s.connect(('localhost',8080)) 
print(s.getsockname()) 
print(s.recv(1024).decode()) 
s.send("acknowledgement recived from the server".encode()) 
```
## OUPUT
![Ex2bCN](https://github.com/user-attachments/assets/35c0f683-d00f-4c5d-a288-e56ab41f3a7d)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
