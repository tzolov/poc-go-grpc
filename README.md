# poc-go-grpc
## protoc

https://developers.google.com/protocol-buffers/docs/reference/go-generated#package
https://grpc.io/docs/languages/go/quickstart/
```
go install google.golang.org/protobuf/cmd/protoc-gen-go@latest
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest
```

```
export PATH="$PATH:$(go env GOPATH)/bin"
```

```
protoc --go_out=. --go_opt=paths=source_relative --go-grpc_out=. --go-grpc_opt=paths=source_relative ./protos/MessageService.proto 
```

form within the `protos` folder:

```
go mod init github.com/tzolov/poc-go-grpc/message
go mod tidy
```

https://medium.com/@adiach3nko/package-management-with-go-modules-the-pragmatic-guide-c831b4eaaf31

```
go mod edit -replace tzolov.net/go-grpc/message=./protos/
go get tzolov.net/go-grpc/message
```

## Docker Image

```
docker build -t tzolov/poc-go-grpc:0.1 .
docker push tzolov/poc-go-grpc:0.1
```

```
docker run -it -p55554:55554 tzolov/poc-go-grpc:0.1
```