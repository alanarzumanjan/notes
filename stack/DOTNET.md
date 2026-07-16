Initialize / Run
```shell
dotnet --info # show SDK/runtime info
dotnet new webapi -n backend # create a new Web API (if needed)
dotnet new webapi -n backend -f net8.0 # create with version
dotnet build # compile
dotnet run  # run once
dotnet watch run # run with hot-reload (auto-restart on changes)
```

EF Core CLI (tools)
```bash
dotnet tool update --global dotnet-ef
dotnet ef --help 
```

Packages
```shell
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Npgsql.EntityFrameworkCore.PostgreSQL
dotnet add package Microsoft.AspNetCore.Authentication.JwtBearer
dotnet add package Microsoft.AspNetCore.Authentication.JwtBearer 
dotnet add package Swashbuckle.AspNetCore

dotnet add package Microsoft.EntityFrameworkCore
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Microsoft.EntityFrameworkCore.Tools

dotnet add package Npgsql
dotnet add package Npgsql.EntityFrameworkCore.PostgreSQL
dotnet add package Microsoft.EntityFrameworkCore.Sqlite

dotnet add package MailKit
dotnet add package MimeKit
dotnet add package BCrypt.Net-Next
dotnet add package DotNetEnv
dotnet add package Microsoft.Extensions.Diagnostics.HealthChecks
```

EF Core: Migrations & Database
```shell
dotnet ef migrations add <name> # scaffold a migration from model changes
dotnet ef migrations remove # remove the last migration (if not applied)
dotnet ef migrations list # list all migrations
dotnet ef database update # apply all pending migrations
dotnet ef database update <Id> # migrate to a specific migration (up/down)
dotnet ef dbcontext info # show DbContext info
dotnet ef dbcontext optimize # (optional) source generators for EF metadata
dotnet ef database drop # drop DB (DEV ONLY)
```

Environment variables
```shell
$env:ASPNETCORE_ENVIRONMENT = "Development" # environment name
$env:ASPNETCORE_URLS = "http://localhost:5000" # hosting URL(s)
$env:ConnectionStrings__Default = "Host=localhost;Port=5432;Database=app;Username=app;Password=***" # DB conn string
$env:ALLOWED_FRONTEND_ORIGIN = "http://localhost:5173"        
# CORS allowed origin
```
