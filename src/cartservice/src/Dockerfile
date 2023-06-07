FROM mcr.microsoft.com/dotnet/sdk:7.0.302@sha256:19c92d0a00d1b66d897bceaa7319bee0dd38a10a851c60bcec9474aa3f01e50f as builder

WORKDIR /app

COPY cartservice.csproj .

RUN dotnet restore cartservice.csproj -r linux-musl-x64

COPY . .

RUN dotnet publish cartservice.csproj -p:PublishSingleFile=true -r linux-musl-x64 --self-contained true -p:PublishTrimmed=True -p:TrimMode=Link -c release -o /cartservice --no-restore

FROM mcr.microsoft.com/dotnet/runtime-deps:7.0.4-alpine3.16-amd64@sha256:7141eea9c7be5f4d2f09df427ba37620e50be150fc93015288b3e26c5071af81 as without-grpc-health-probe-bin

WORKDIR /app

COPY --from=builder /cartservice .

EXPOSE 7070

ENTRYPOINT ["/app/cartservice"]
