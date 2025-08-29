# Echoserver - Echo server and client using python socket

# AIM:
To develop a simple webserver to serve html programming pages.

## DESIGN STEPS:

### Step 1: HTML content creation is done
### Step 2: Design of webserver workflow
### Step 3: Implementation using Python code
### Step 4: Serving the HTML pages.
### Step 5: Testing the webserver

## PROGRAM:

### CLIENT : - 
```
import socket


HOST = "127.0.0.1"  # The server's hostname or IP address
PORT = 65432  # The port used by the server


with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.connect((HOST, PORT))
    s.sendall(b"Hello SEC")
    data = s.recv(1024)


print(f"Received {data!r}")
```

### SERVER : - 
```
import socket
HOST = '127.0.0.1' 
PORT = 65432 
with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.bind((HOST, PORT))
    s.listen()
    print(f"Server started. Listening on {HOST}:{PORT}...")
    conn, addr = s.accept()
    with conn:
        print(f"Connected by {addr}")
        while True:
            data = conn.recv(1024)
            if not data:
                break
            conn.sendall(data)
```

##  Architecture Diagram

```bash
+--------------------------+
|  User's Web Browser      |
|  (Client: Chrome/Firefox)|
+-----------+--------------+
            |
            |  HTTP Request (GET /)
            v
+-----------+--------------+
|   Python Web Server      |
| (http.server + Handler)  |
| - Listens on Port 8000   |
| - Handles GET Requests   |
| - Sends HTML Response    |
+-----------+--------------+
            |
            |  HTML Response
            v
+--------------------------+
|  User Sees Rendered Page |
|  <h1>Hello Web Server</h1>|
+--------------------------+
```

## OUTPUT:

### CLIENT OUTPUT:

<img width="1919" height="1079" alt="ex1opclient" src="https://github.com/user-attachments/assets/44533479-4602-410d-93da-3bdbf917e55c" />

### SERVER OUTPUT:

<img width="1919" height="1079" alt="ex1opserver" src="https://github.com/user-attachments/assets/4c58a451-7992-4ed7-bb82-c18b452ba99f" />

## RESULT:
Thus, the program is executed succesfully.
