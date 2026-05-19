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
## SERVER
~~~
import socket

# Create socket
s = socket.socket()

# Host and port
host = socket.gethostname()
port = 60000

# Bind socket
s.bind((host, port))

# Listen for connection
s.listen(5)
print("Server waiting for connection...")

# Accept client connection
c, addr = s.accept()
print("Connected to:", addr)

# Receive client message
print(c.recv(1024).decode())

# Open file and send data
filename = "sample.txt"

with open(filename, "rb") as f:
    data = f.read(1024)

    while data:
        c.send(data)
        data = f.read(1024)

print("File sent successfully")

# Close connection
c.close()
s.close()
print("Connection closed")
~~~

## CLIENT
~~~
import socket

# Create socket
s = socket.socket()

# Host and port
host = socket.gethostname()
port = 60000

# Connect to server
s.connect((host, port))

# Send message to server
s.send("Hello server!".encode())

# Receive file
with open("received_file.txt", "wb") as f:

    while True:
        print("Receiving data...")

        data = s.recv(1024)

        print("data =", data)

        # Stop when no data received
        if not data:
            break

        f.write(data)

print("Successfully got the file")

# Close socket
s.close()

print("Connection closed")
~~~

## OUPUT

## SERVER 
<img width="340" height="97" alt="image" src="https://github.com/user-attachments/assets/f9a215c1-6398-4351-ab5f-5e0212605945" />
## CLIENT 
<img width="818" height="113" alt="image" src="https://github.com/user-attachments/assets/1fdef274-6c44-40ae-bff3-11bc8ed6307f" />

## RESULT 
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
