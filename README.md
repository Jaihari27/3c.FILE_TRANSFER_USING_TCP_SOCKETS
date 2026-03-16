# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
Server
```
import socket

host = '127.0.0.1'
port = 6000

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind((host, port))
server_socket.listen(1)

print("Server waiting for connection...")
conn, addr = server_socket.accept()
print("Connected to:", addr)

filename = "sample.txt"

with open("doc.txt", "rb") as file:
    data = file.read()
    conn.send(data).encode()

print("File sent successfully")
conn.close()
server_socket.close()
```
Client
```
import socket

host = '127.0.0.1'
port = 6000

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect((host, port))

with open("received_file.txt", "wb") as file:
    while True:
        data = client_socket.recv(1024)
        if not data:
            break
        file.write(data)

print("File received successfully")
client_socket.close()
```
## OUPUT
Server
<img width="1303" height="92" alt="image" src="https://github.com/user-attachments/assets/64a080b8-dcdc-4369-8678-b2bd2d78389e" />
Client
<img width="1306" height="72" alt="image" src="https://github.com/user-attachments/assets/4b327f91-e9c0-4910-b598-a023fcd91407" />
Received Files
<img width="455" height="117" alt="image" src="https://github.com/user-attachments/assets/c5b26f81-5836-4777-9c50-f0174df89328" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
