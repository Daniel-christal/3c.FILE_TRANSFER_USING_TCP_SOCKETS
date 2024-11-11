![image](https://github.com/user-attachments/assets/fdebe7b1-c44e-4f43-8fd6-42fa31dad1a8)![image](https://github.com/user-attachments/assets/e414d125-29d4-4328-ba1d-d7f7af7b327e)# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM:
```
Developed By:Daniel C
Reg No:212223240023
```
# Server:
```
import socket

def send_file(filename, client_socket):
    with open(filename, 'rb') as file:
        for data in file:
            client_socket.sendall(data)

def start_server():
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind(('127.0.0.1', 5555))
    server_socket.listen(5)
    print("Server started, listening on port 5555")

    while True:
        client_socket, addr = server_socket.accept()
        print(f"Accepted connection from {addr}")

        filename = input("Enter filename to send: ")
        try:
            send_file(filename, client_socket)
            print(f"File '{filename}' sent successfully")
        except FileNotFoundError:
            print(f"File '{filename}' not found")

        client_socket.close()

start_server()
```
# Client:
```
import socket

def receive_file(filename, server_socket):
    with open(filename, 'wb') as file:
        while True:
            data = server_socket.recv(1024)
            if not data:
                break
            file.write(data)

def start_client():
    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client_socket.connect(('127.0.0.1', 5555))

    filename = input("Enter filename to save: ")
    client_socket.sendall(filename.encode())

    receive_file(filename, client_socket)
    print(f"File '{filename}' received successfully")

    client_socket.close()

start_client()
```
## OUPUT:
# Server:
![image](https://github.com/user-attachments/assets/fad1fceb-d1f3-4b06-a122-efa75fb14258)

# Client:
![image](https://github.com/user-attachments/assets/2a90c5e7-f3b9-4bc6-9ee7-a82d20bdbc07)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
