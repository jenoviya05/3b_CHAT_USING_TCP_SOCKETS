# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
server.py
```
3b# chat_server.py

import socket

# Create socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind address and port
server_socket.bind(("localhost", 5000))

# Listen for connection
server_socket.listen(1)

print("Waiting for client connection...")

# Accept connection
conn, addr = server_socket.accept()

print("Connected with:", addr)

while True:
    # Receive message from client
    client_msg = conn.recv(1024).decode()
    print("Client:", client_msg)

    # Exit condition
    if client_msg.lower() == "bye":
        break

    # Send message to client
    msg = input("Server: ")
    conn.send(msg.encode())

    if msg.lower() == "bye":
        break

# Close connection
conn.close()
server_socket.close()

```
client.py
```
3b# chat_client.py

import socket

# Create socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Connect to server
client_socket.connect(("localhost", 5000))

print("Connected to server")

while True:
    # Send message to server
    msg = input("Client: ")
    client_socket.send(msg.encode())

    if msg.lower() == "bye":
        break

    # Receive message from server
    server_msg = client_socket.recv(1024).decode()
    print("Server:", server_msg)

    if server_msg.lower() == "bye":
        break

# Close socket
client_socket.close()
```
## OUPUT
<img width="1919" height="1109" alt="Screenshot 2026-05-20 092038" src="https://github.com/user-attachments/assets/c3f18f98-fb55-46f6-94d9-4b677a9b80cc" />

<img width="1915" height="1041" alt="Screenshot 2026-05-20 092054" src="https://github.com/user-attachments/assets/4e8b8454-d81c-463d-9b99-5074c267326a" />


## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
