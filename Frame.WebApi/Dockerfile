FROM mcr.microsoft.com/dotnet/framework/sdk:4.8 AS build
WORKDIR /src

COPY . .
RUN dotnet restore Condotframe.sln

RUN dotnet publish Frame.WebApi/Frame.WebApi.csproj -c Release -o out --no-restore

FROM mcr.microsoft.com/dotnet/framework/runtime:4.8
WORKDIR /app

COPY --from=build /src/out .
ENTRYPOINT ["Frame.WebApi.exe"]
