FROM mcr.microsoft.com/dotnet/sdk:5.0.100-rc.2 AS build-env
WORKDIR /app

# Copiar csproj e restaurar dependencias
COPY *.csproj ./
RUN dotnet restore

# Build da aplicacao
COPY . ./
RUN dotnet publish -c Release -o out

# Build da imagem
FROM mcr.microsoft.com/dotnet/aspnet:5.0.0-rc.2
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "APIFinancas.dll"]