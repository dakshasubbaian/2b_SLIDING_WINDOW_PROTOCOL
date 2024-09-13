# Ex:2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
### Name:Daksha Subbaian
### Register Number:212223230036
## AIM
To write a python program for Implementation of sliding Window Protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM:
## Client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s
```
## Server
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement received from the server".encode())
```
## OUTPUT:
## Client:
![image](https://github.com/user-attachments/assets/19f0b47d-1b27-4be9-a99f-b40a13dc7866)

## Server:
![image](https://github.com/user-attachments/assets/0c894bb8-cd75-40e1-af19-637dba766458)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
