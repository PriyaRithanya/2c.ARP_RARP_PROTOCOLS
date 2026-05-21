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
client side:
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
server side:
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True: 
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())
## OUPUT - ARP
<img width="838" height="608" alt="Screenshot (162)" src="https://github.com/user-attachments/assets/c4094f2e-699e-4226-adcf-aad52a7c07da" />
<img width="756" height="496" alt="Screenshot (163)" src="https://github.com/user-attachments/assets/b0875dbe-7a26-4d9b-9ae8-24f753d252a8" />


## PROGRAM - RARP
client side:
import socket
s = socket.socket()
s.connect(('localhost',9000))
while True:
    ip = input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address", s.recv(1024).decode())
server side:
import socket
s = socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c, addr = s.accept()
address = { "6A:08:AA:C2":"192.168.1.100", "A:BC:E3:FA":"192.168.1.99"}
while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
## OUPUT -RARP
<img width="1578" height="910" alt="Screenshot (160)" src="https://github.com/user-attachments/assets/0a32f806-637f-4558-90a6-a010573dcbe5" />
<img width="1519" height="789" alt="Screenshot (166)" src="https://github.com/user-attachments/assets/d81e211e-1604-4715-84f8-a210cab8aae1" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
