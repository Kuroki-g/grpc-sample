# gRPC on ASP.NET Core
This is tutorial code from Microsoft's official site.

https://learn.microsoft.com/ja-jp/aspnet/core/tutorials/grpc/grpc-start?view=aspnetcore-8.0&tabs=visual-studio-code

## Run Server

Server

```bash
dotnet run --launch-profile https
```

Client

```bash
dotnet run
```

Server側では以下のように表示されます。

```bash
info: Microsoft.AspNetCore.Hosting.Diagnostics[1]
      Request starting HTTP/2 POST https://localhost:7279/greet.Greeter/SayHello - application/grpc -
info: Microsoft.AspNetCore.Routing.EndpointMiddleware[0]
      Executing endpoint 'gRPC - /greet.Greeter/SayHello'
info: Microsoft.AspNetCore.Routing.EndpointMiddleware[1]
      Executed endpoint 'gRPC - /greet.Greeter/SayHello'
info: Microsoft.AspNetCore.Hosting.Diagnostics[2]
      Request finished HTTP/2 POST https://localhost:7279/greet.Greeter/SayHello - 200 - application/grpc 68.0024ms
```

## Check service
See: https://learn.microsoft.com/ja-jp/aspnet/core/grpc/test-tools?view=aspnetcore-9.0#discover-services

```bash
$ grpcurl -insecure localhost:7279 list
greet.Greeter
grpc.reflection.v1alpha.ServerReflection
```

```bash
$ grpcurl -insecure localhost:7279 describe 
greet.Greeter is a service:
service Greeter {
  rpc SayHello ( .greet.HelloRequest ) returns ( .greet.HelloReply );
}
grpc.reflection.v1alpha.ServerReflection is a service:
service ServerReflection {
  rpc ServerReflectionInfo ( stream .grpc.reflection.v1alpha.ServerReflectionRequest ) returns ( stream .grpc.reflection.v1alpha.ServerReflectionResponse );
}
```

```bash
grpcurl -insecure localhost:7279 describe greet.Greeter
```

```bash
$ grpcurl -insecure localhost:7279 describe greet.Greeter
greet.Greeter is a service:
service Greeter {
  rpc SayHello ( .greet.HelloRequest ) returns ( .greet.HelloReply );
}
```

Check request type:

```bash
$ grpcurl -insecure localhost:7279 describe greet.HelloRequest
greet.HelloRequest is a message:
message HelloRequest {
  string name = 1;
}
```

```bash
$ grpcurl -d '{ "name": "World" }' -insecure localhost:7279 greet.Greeter.SayHello
{
  "message": "Hello World"
}
```