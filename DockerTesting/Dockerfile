FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build

WORKDIR /src

COPY . .

RUN dotnet publish "DockerTesting.csproj" -o /published /p:UseAppHost=false



FROM mcr.microsoft.com/dotnet/aspnet:10.0

WORKDIR /app

ENV ASPNETCORE_ENVIRONMENT=Development

COPY --from=build /published .

ENTRYPOINT [ "dotnet", "DockerTesting.dll" ]