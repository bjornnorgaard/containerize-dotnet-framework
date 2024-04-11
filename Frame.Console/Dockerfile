FROM mcr.microsoft.com/dotnet/framework/sdk:4.8 AS build
WORKDIR /src

COPY *.sln ./
COPY */*.csproj ./

RUN nuget restore

COPY . .

RUN msbuild Frame.Console/Frame.Console.csproj /p:Configuration=Release /p:OutputPath=out

FROM mcr.microsoft.com/dotnet/framework/runtime:4.8
WORKDIR /app

COPY --from=build /src/Frame.Console/out ./
ENTRYPOINT ["Frame.Console.exe"]
