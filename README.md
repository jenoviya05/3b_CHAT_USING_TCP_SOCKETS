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
~~~
import socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind(("localhost", 5000))


server_socket.listen(1)

print("Waiting for client connection...")


conn, addr = server_socket.accept()

print("Connected with:", addr)

while True:
    
    client_msg = conn.recv(1024).decode()
    print("Client:", client_msg)

   
    if client_msg.lower() == "bye":
        break

    
    msg = input("Server: ")
    conn.send(msg.encode())

    if msg.lower() == "bye":
        break


conn.close()
server_socket.close()
~~~
client.py
~~~
import socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

client_socket.connect(("localhost", 5000))

print("Connected to server")

while True:
    
    msg = input("Client: ")
    client_socket.send(msg.encode())

    if msg.lower() == "bye":
        break

    
    server_msg = client_socket.recv(1024).decode()
    print("Server:", server_msg)

    if server_msg.lower() == "bye":
        break

client_socket.close()
~~~
## OUPUT
server.py
<img width="1860" height="267" alt="Screenshot 2026-05-20 090724" src="https://github.com/user-attachments/assets/b831b755-91fe-4403-8755-e6f77743644b" />
client.py
<img width="1882" height="285" alt="Screenshot 2026-05-20 090738" src="https://github.com/user-attachments/assets/bf5c6708-0b07-4c9d-ab27-b2568ce89c35" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
