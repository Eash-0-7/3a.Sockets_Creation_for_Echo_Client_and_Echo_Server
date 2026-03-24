# 3a.CREATION FOR ECHO CLIENT AND ECHO SERVER USING TCP SOCKETS
# AIM
To write a python program for creating Echo Client and Echo Server using TCP
Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server .
4. Send and receive the message using the send function in socket.
## PROGRAM
1. server.py
```
import socket

# Create socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind
host = '127.0.0.1'
port = 12345
server_socket.bind((host, port))

# Listen
server_socket.listen(1)
print("Echo Server is waiting for connection...")

# Accept connection
conn, addr = server_socket.accept()
print("Connected to:", addr)

while True:
    # Receive message
    data = conn.recv(1024).decode()
    
    if not data:
        break
    
    print("Client:", data)
    
    # Echo back same message
    conn.send(data.encode())

# Close connection
conn.close()
server_socket.close()
```
2. client.py
```
import socket

# Create socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Connect to server
host = '127.0.0.1'
port = 12345
client_socket.connect((host, port))

while True:
    # Take input from user
    msg = input("Enter message: ")
    
    if msg.lower() == 'exit':
        break
    
    # Send message
    client_socket.send(msg.encode())
    
    # Receive echo
    data = client_socket.recv(1024).decode()
    print("Echo from server:", data)

# Close connection
client_socket.close()
```
## OUPUT
<img width="1029" height="155" alt="image" src="https://github.com/user-attachments/assets/4e57a2cf-df2d-4186-9b65-299a9e0a1763" />

<img width="1022" height="197" alt="image" src="https://github.com/user-attachments/assets/a654f3c5-5701-45a8-8b13-d9e189876b05" />

## RESULT
Thus, the python program for creating Echo Client and Echo Server using TCP Sockets Links 
was successfully created and executed.
