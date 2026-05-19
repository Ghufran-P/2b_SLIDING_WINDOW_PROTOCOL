# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
### SERVER.PY
```
import socket 
s=socket.socket() 
s.bind(('localhost',8000)) 
s.listen(5) 
c,addr=s.accept()
l=["How","Are","You ?","I","am","fine!"]
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
### CLIENT.PY
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("Message recived".encode())
```
## OUPUT
### SERVER.PY
<img width="530" height="150" alt="592511463-01adb3ab-f274-4438-b4a7-cd26cf468877" src="https://github.com/user-attachments/assets/fa32adc6-c0c8-4884-9f9b-510730af45a5" />

### CLIENT.PY
<img width="487" height="177" alt="592511640-27cde1bb-2df0-4d5a-acc4-38bd515d3727" src="https://github.com/user-attachments/assets/0c0ba54f-165b-47ae-ab21-63d6cb29947b" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
