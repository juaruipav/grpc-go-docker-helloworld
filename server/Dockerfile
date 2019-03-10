# GRPC-demo
# build command : docker build . -t grpc-demo/server
# run command : docker run -it grpc-demo/server
FROM golang:latest

# Install grpc
RUN go get -u google.golang.org/grpc && \
    go get -u github.com/golang/protobuf/protoc-gen-go

# Install protoc and zip system library
RUN apt-get update && apt-get install -y zip && \
    mkdir /opt/protoc && cd /opt/protoc && wget https://github.com/protocolbuffers/protobuf/releases/download/v3.7.0/protoc-3.7.0-linux-x86_64.zip && \
    unzip protoc-3.7.0-linux-x86_64.zip

ENV PATH=$PATH:$GOPATH/bin:/opt/protoc/bin

# Copy the grpc proto file and generate the go module
RUN mkdir -p /go/src/helloworld
COPY helloworld.proto /go/src/helloworld
RUN cd /go/src && \
    protoc -I helloworld/ helloworld/helloworld.proto --go_out=plugins=grpc:helloworld

# Copy the project to be executed
RUN mkdir -p /go/src/grpc-server 
COPY main.go /go/src/grpc-server

ENTRYPOINT cd /go/src/grpc-server && go run main.go