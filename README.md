## 
This is a multi-user online chat system implemented using Golang network programming, with high concurrency achieved using goroutine and user registration information saved with redis.
Project Directory：
```
.
├── README.md
├── client // client-side code
│   ├── logger // custom log printer
│   │   └── logger.go
│   ├── main.go
│   ├── model
│   │   └── user.go
│   ├── process // Handle the connection with the server, send and receive messages
│   │   ├── messageProcess.go
│   │   ├── serverProcess.go
│   │   └── userProcess.go
│   └── utils
│       └── utils.go
├── common // Shared code between client and server, mainly used to define the message of the communication agreement between client and server
│   └── message
│       └── message.go
├── config // configuration information
│   ├── config.go
│   └── config.json
└── server // server-side code
    ├── main 
    │   ├── main.go
    │   └── redis.go
    ├── model 
    │   ├── clientConn.go
    │   ├── error.go
    │   ├── user.go
    │   └── userDao.go
    ├── process // Handle the connection with client, send and receive messages
    │   ├── groupMessageProcess.go // process group message
    │   ├── onlineInfoProcess.go // display online users
    │   ├── pointToPointMessageProcess.go // process point to point messages
    │   ├── processor.go // entry to message handler
    │   └── userProcess.go // Handle messages related to user login and signup
    └── utils
        └── utils.go
```

The server and client codes are basically independent. The server directory is the server code, the client directory is the client code, and the packages in the common directory are shared by the server and the client.

## Demo
### sign up
![sign-up](https://github.com/ItsWewin/images/raw/master/Chat/sign-up.png)

### log in
![sign-in](https://raw.githubusercontent.com/ItsWewin/images/master/Chat/sign-in.png)

### display list of online users
![online-user-list](https://github.com/ItsWewin/images/raw/master/Chat/online-user-list.png)
### group message
![group-message-1.png](https://github.com/ItsWewin/images/raw/master/Chat/group-message-1.png)
![group-message-2.png](https://github.com/ItsWewin/images/raw/master/Chat/group-message-2.png)
### private message(point to point communication)
![point-to-point.png](https://github.com/ItsWewin/images/raw/master/Chat/point-to-point.png)
![point-to-point2.png](https://github.com/ItsWewin/images/raw/master/Chat/point-to-point2.png)

------------------------------------------------------------------------------------------------------------------------------

## usage (installed Go environment required)

### clone this project to your GOPATH

```
cd ${GOPATH}/src
git clone git@github.com:weicaivi/GoChat.git
```

### build server and run

```
go build -o server gochat/server/main
./server
```

### build client and run
```
go build -o client gochat/client
./client
```

### Function of this demo
1. User register
2. User login
3. User send group message
4. Display online user list
5. Point-to-point communication
6. Print messages in different colors according to their type (info, notice, warn, error, success) (supported by both Unix and window)
