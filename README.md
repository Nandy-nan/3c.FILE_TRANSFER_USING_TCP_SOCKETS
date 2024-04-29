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
NANDHANA.R
212223040124
```
CLIENT:
import socket

s = socket.socket()

host = socket.gethostname()
port = 60000

s.connect((host, port))
s.send("Hello server!".encode())

with open('received_file', 'wb') as f:
    print('receiving data...')
    while True:
        data = s.recv(1024)
        print('data=%s', (data))
        if not data:
            break
        f.write(data)

print('Successfully received the file')
s.close()
print('connection closed')

SERVER:
import socket

port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)

print("Server listening on port", port)

while True:
    conn, addr = s.accept()
    print("Connected to", addr)
    
    data = conn.recv(1024)
    print('Server received', repr(data))

    filename = 'D:\\Saveetha\\19CS406 Computer Networks\\Ex3c\\mytext.txt'
    with open(filename, 'rb') as f:
        l = f.read(1024)
        while l:
            conn.send(l)
            print('Sent', repr(l))
            l = f.read(1024)
    
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
```
## OUPUT

![Screenshot 2024-04-29 140858](https://github.com/Nandy-nan/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/153698914/2776f39a-7fea-417d-a23d-5d3b83ef7dee)

![Screenshot 2024-04-29 141232](https://github.com/Nandy-nan/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/153698914/e5ecc56a-f3f0-472a-8c40-1290ae44befd)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
