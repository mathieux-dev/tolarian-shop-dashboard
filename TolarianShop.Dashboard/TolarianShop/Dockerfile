# Etapa 1: Construir a aplica��o
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app
EXPOSE 80

# Copie o arquivo csproj e restaure as depend�ncias
COPY *.csproj ./
RUN dotnet restore

# Copie o restante do c�digo e compile
COPY . ./
RUN dotnet publish -c Release -o /out

# Etapa 2: Executar a aplica��o
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app
COPY --from=build /out ./
ENTRYPOINT ["dotnet", "TolarianShop.dll"]
