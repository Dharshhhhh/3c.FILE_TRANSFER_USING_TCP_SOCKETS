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
## server
```
import socket

HOST = "127.0.0.1"
PORT = 65432

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as server_socket:
    server_socket.bind((HOST, PORT))
    server_socket.listen()

    print(f"Server is listening on {HOST}:{PORT}")
    while True:
        conn, addr = server_socket.accept()
        with conn:
            print(f"Connected by {addr}")
            while True:
                data = conn.recv(1024)
                if not data:
                    break
                conn.sendall(data)
                print(f"Echoed: {data.decode('utf-8')}")
```
## client 
```
import socket

HOST = "127.0.0.1"
PORT = 65432

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as client_socket:
    client_socket.connect((HOST, PORT))

    message = "Hello, Server!"
    client_socket.sendall(message.encode("utf-8"))

    data = client_socket.recv(1024)
    print(f"Received echo: {data.decode('utf-8')}")
```
## OUPUT
![WhatsApp Image 2025-11-14 at 10 05 06_e59277a6](https://github.com/user-attachments/assets/c726467e-29ab-4553-aa0f-a9cb9a804f80)
 
## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
