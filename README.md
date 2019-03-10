# GRPC-GO-DOCKER-HELLOWORLD

The objective of this repository is quite simple: to recreate the examples from [here](https://github.com/grpc/grpc-go/tree/master/examples/helloworld) in a docker environment running in localhost.

Just execute the following commands:

Run the server:
```
$ cd server 
$ docker build . -t grpc-demo/server
$ docker run --net=host -it grpc-demo/server 
```


Run the client:
```
$ cd client 
$ docker build . -t grpc-demo/client
$ docker run --net=host -it grpc-demo/client 
```

