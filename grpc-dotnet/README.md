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
