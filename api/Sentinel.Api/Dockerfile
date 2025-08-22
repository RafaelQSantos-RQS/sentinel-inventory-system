# Etapa 1: build
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /app

# Copia csproj e restaura dependências
COPY *.csproj ./
RUN dotnet restore

# Copia todo o restante e builda
COPY . ./
RUN dotnet publish -c Release -o out

# Etapa 2: runtime
FROM mcr.microsoft.com/dotnet/aspnet:9.0
WORKDIR /app
COPY --from=build /app/out .

# Expõe porta 8080
EXPOSE 8080

# Comando para iniciar a API
ENTRYPOINT ["dotnet", "Sentinel.Api.dll"]
