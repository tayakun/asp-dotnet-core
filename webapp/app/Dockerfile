FROM mcr.microsoft.com/dotnet/aspnet:3.1-alpine AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:3.1-alpine AS build
WORKDIR /src
COPY [ "app.csproj", "./" ]
RUN dotnet restore "app.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "app.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "app.csproj" -c Release -o /app/publish

FROM build AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENV ASPNETCORE_URLS http://*:5000
ENV LANG ja_jp.utf8
ENTRYPOINT [ "dotnet", "app.dll" ]
